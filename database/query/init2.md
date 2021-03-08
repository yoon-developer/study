-- COUNT특정 열의 행 수를 계산 하는 SQL 집계 함수 입니다.
``` sql
SELECT
  COUNT(*)
FROM
  tutorial.aapl_historical_stock_price;
```

-- high 값이 null이 아닌 모든 행의 수 조회
``` sql
SELECT
  COUNT(high)
FROM
  tutorial.aapl_historical_stock_price;
```

``` sql
SELECT
  COUNT(date) AS count_of_date
FROM
  tutorial.aapl_historical_stock_price;
```

``` sql
SELECT
  COUNT(date) AS "Count Of Date"
FROM
  tutorial.aapl_historical_stock_price;
```

-- SUM 함수 (null 은 0 으로 취급)
``` sql
SELECT
  SUM(volume)
FROM
  tutorial.aapl_historical_stock_price;
```

-- MIN, MAX
``` sql
SELECT
  MIN(volume) AS min_volume,
  MAX(volume) AS max_volume
FROM
  tutorial.aapl_historical_stock_price;
```

-- AVG
``` sql
SELECT
  AVG(high)
FROM
  tutorial.aapl_historical_stock_price
WHERE
  'high' IS NOT NULL;
```

-- GROUP
``` sql
SELECT
  year,
  COUNT(*) AS count
FROM
  tutorial.aapl_historical_stock_price
GROUP BY
  year;
```

``` sql
SELECT
  year,
  MONTH,
  COUNT(*) AS count
FROM
  tutorial.aapl_historical_stock_price
GROUP BY
  year,
  MONTH;
```

-- GROUP 열 번호
``` sql
SELECT
  year,
  MONTH,
  COUNT(*) AS count
FROM
  tutorial.aapl_historical_stock_price
GROUP BY
  1,
  2;
```

-- GROUP BY, ORDER BY 사용
``` sql
SELECT
  year,
  MONTH,
  COUNT(*) AS count
FROM
  tutorial.aapl_historical_stock_price
GROUP BY
  MONTH,
  year
ORDER BY
  year DESC,
  MONTH;
```

-- HAVING 특정 데이터 이상 조회
``` sql
SELECT
  year,
  MONTH,
  MAX(high) AS month_high
FROM
  tutorial.aapl_historical_stock_price
GROUP BY
  year,
  MONTH
HAVING
  MAX(high) > 400
ORDER BY
  year,
  MONTH;
```

-- CASE
``` sql
SELECT
  player_name,
  year,
  CASE
    WHEN year = 'SR' THEN 'yes'
    ELSE NULL
  END AS is_a_senior
FROM
  benn.college_football_players;
```

``` sql
SELECT
  player_name,
  year,
  CASE
    WHEN year = 'SR' THEN 'yes'
    ELSE 'no'
  END AS is_a_senior
FROM
  benn.college_football_players;
```

-- CASE 다중 조건
``` sql
SELECT
  player_name,
  year,
  CASE
    WHEN weight > 250 THEN 'over 250'
    WHEN weight > 200 THEN '201-250'
    WHEN weight > 175 THEN '176-200'
    ELSE '175 or under'
  END AS weight_group
FROM
  benn.college_football_players;
```

``` sql
SELECT
  player_name,
  year,
  CASE
    WHEN weight > 250 THEN 'over 250'
    WHEN weight > 200
    AND weight <= 250 THEN '201-250'
    WHEN weight > 175
    AND weight <= 200 THEN '176-200'
    ELSE '175 or under'
  END AS weight_group
FROM
  benn.college_football_players;
```

``` sql
SELECT
  player_name,
  CASE
    WHEN year = 'FR'
    AND position = 'WR' THEN 'frosh_wr'
    ELSE NULL
  END AS sample_case_statement
FROM
  benn.college_football_players;
```

-- CASE 집계 함수 사용
``` sql
SELECT
  CASE
    WHEN year = 'FR' THEN 'FR'
    ELSE 'Not FR'
  END AS year_group,
  COUNT(*) AS count
FROM
  benn.college_football_players
GROUP BY
  CASE
    WHEN year = 'FR' THEN 'FR'
    ELSE 'Not FR'
  END;
```

``` sql
SELECT
  COUNT(*) AS fr_count
FROM
  benn.college_football_players
WHERE
  year = 'FR';
```

``` sql
SELECT
  CASE
    WHEN year = 'FR' THEN 'FR'
    WHEN year = 'SO' THEN 'SO'
    WHEN year = 'JR' THEN 'JR'
    WHEN year = 'SR' THEN 'SR'
    ELSE 'No Year Data'
  END AS year_group,
  COUNT(*) AS count
FROM
  benn.college_football_players
GROUP BY
  1;
```

``` sql
SELECT
  CASE
    WHEN year = 'FR' THEN 'FR'
    WHEN year = 'SO' THEN 'SO'
    WHEN year = 'JR' THEN 'JR'
    WHEN year = 'SR' THEN 'SR'
    ELSE 'No Year Data'
  END AS year_group,
  COUNT(*) AS count
FROM
  benn.college_football_players
GROUP BY
  year_group;
```
  
``` sql
SELECT
  CASE
    WHEN year = 'FR' THEN 'FR'
    WHEN year = 'SO' THEN 'SO'
    WHEN year = 'JR' THEN 'JR'
    WHEN year = 'SR' THEN 'SR'
    ELSE 'No Year Data' END AS year_group,
    COUNT(*) AS count
FROM benn.college_football_players
GROUP BY
  CASE
    WHEN year = 'FR' THEN 'FR'
    WHEN year = 'SO' THEN 'SO'
    WHEN year = 'JR' THEN 'JR'
    WHEN year = 'SR' THEN 'SR'
    ELSE 'No Year Data' END;
```
    
``` sql
SELECT
  CASE
    WHEN year = 'FR' THEN 'FR'
    WHEN year = 'SO' THEN 'SO'
    WHEN year = 'JR' THEN 'JR'
    WHEN year = 'SR' THEN 'SR'
    ELSE 'No Year Data' END AS year_group,
    *
FROM benn.college_football_players;
```

-- 집계 함수 내에서 CASE 사용
``` sql
SELECT
  CASE
    WHEN year = 'FR' THEN 'FR'
    WHEN year = 'SO' THEN 'SO'
    WHEN year = 'JR' THEN 'JR'
    WHEN year = 'SR' THEN 'SR'
    ELSE 'No Year Data' END AS year_group,
    COUNT(*) AS count
FROM benn.college_football_players
  GROUP BY 1;
```
  
-- 수평으로 방향 변경 
``` sql
SELECT COUNT(CASE WHEN year = 'FR' THEN 1 ELSE NULL END) AS fr_count,
     COUNT(CASE WHEN year = 'SO' THEN 1 ELSE NULL END) AS so_count,
     COUNT(CASE WHEN year = 'JR' THEN 1 ELSE NULL END) AS jr_count,
     COUNT(CASE WHEN year = 'SR' THEN 1 ELSE NULL END) AS sr_count
FROM benn.college_football_players;
```