-- 전체 조회
``` sql
SELECT
  *
FROM
  tutorial.us_housing_units;
```

-- 이름 변경 하여 출력
``` sql
SELECT
  west AS West_Region,
  south AS South_Region
FROM
  tutorial.us_housing_units;
```

-- Select 개수 지정
``` sql
SELECT
  *
FROM
  tutorial.us_housing_units
LIMIT
  10;
```

-- 특정 데이터 값 컬럼 조회
``` sql
SELECT
  *
FROM
  tutorial.us_housing_units
WHERE
  MONTH = 1;
```

-- 특정 데이터 이상인 값 컬럼 조회
``` sql
SELECT
  *
FROM
  tutorial.us_housing_units
WHERE
  west > 30;
```

-- 특정 데이터 값이 아닌 컬럼 조회
``` sql
SELECT
  *
FROM
  tutorial.us_housing_units
WHERE
  month_name != 'January';
```

-- 특정 데이터 값의 알파벳 순서의 따라 필터 하여 컬럼 조회
``` sql
SELECT
  *
FROM
  tutorial.us_housing_units
WHERE
  month_name > 'January';
```

``` sql
SELECT
  *
FROM
  tutorial.us_housing_units
WHERE
  month_name > 'J';
```

-- 산술 계산
``` sql
SELECT
  year,
  MONTH,
  west,
  south,
  west + south AS south_plus_west
FROM
  tutorial.us_housing_units;
```

``` sql
SELECT
  year,
  MONTH,
  west,
  south,
  west + south - 4 * year AS nonsense_column
FROM
  tutorial.us_housing_units;
```

``` sql
SELECT
  year,
  MONTH,
  west,
  south,
  (west + south) / 2 AS south_west_avg
FROM
  tutorial.us_housing_units;
```

-- 논리 연산자
``` sql
SELECT
  *
FROM
  tutorial.billboard_top_100_year_end
ORDER BY
  year DESC,
  year_rank;
```

-- LIKE SQL 의 논리 연산자 로 정확한 값이 아닌 유사한 값을 일치시킬 수 있습니다.
``` sql
SELECT
  *
FROM
  tutorial.billboard_top_100_year_end
WHERE
  "group" LIKE 'Snoop%';
```

-- LIKE SQL 대소문자 무시
``` sql
SELECT
  *
FROM
  tutorial.billboard_top_100_year_end
WHERE
  "group" ILIKE 'snoop%';
```

-- IN결과에 포함 할 값 목록을 지정할 수있는 SQL 의 논리 연산자 입니다. 
``` sql
SELECT
  *
FROM
  tutorial.billboard_top_100_year_end
WHERE
  year_rank IN (1, 2, 3);
```

``` sql
SELECT
  *
FROM
  tutorial.billboard_top_100_year_end
WHERE
  artist IN ('Taylor Swift', 'Usher', 'Ludacris');
```

-- BETWEEN특정 범위 내에있는 행만 선택할 수있는 SQL 의 논리 연산자 입니다.
``` sql
SELECT
  *
FROM
  tutorial.billboard_top_100_year_end
WHERE
  year_rank BETWEEN 5
  AND 10;
```

``` sql
SELECT
  *
FROM
  tutorial.billboard_top_100_year_end
WHERE
  year_rank >= 5
  AND year_rank <= 10;
```

-- IS NULL결측 데이터가있는 행을 결과에서 제외 할 수있는 SQL 의 논리 연산자 입니다.
``` sql
SELECT
  *
FROM
  tutorial.billboard_top_100_year_end
WHERE
  artist IS NULL;
```

-- AND두 조건을 만족하는 행만 선택할 수있는 SQL 의 논리 연산자 입니다. 
``` sql
SELECT
  *
FROM
  tutorial.billboard_top_100_year_end
WHERE
  year = 2012
  AND year_rank <= 10;
```

``` sql
SELECT
  *
FROM
  tutorial.billboard_top_100_year_end
WHERE
  year = 2012
  AND year_rank <= 10
  AND "group" ILIKE '%feat%';
```

-- OR두 조건 중 하나를 만족하는 행을 선택할 수있는 SQL 의 논리 연산자 입니다.
``` sql
SELECT
  *
FROM
  tutorial.billboard_top_100_year_end
WHERE
  year_rank = 5
  OR artist = 'Gotye';
```

``` sql
SELECT
  *
FROM
  tutorial.billboard_top_100_year_end
WHERE
  year = 2013
  AND (
    "group" ILIKE '%macklemore%'
    OR "group" ILIKE '%timberlake%'
  );
```

-- NOT SQL 의 논리 연산자로 , 조건문 앞에 해당 명령문이 거짓 인 행을 선택할 수 있습니다.
``` sql
SELECT
  *
FROM
  tutorial.billboard_top_100_year_end
WHERE
  year = 2013
  AND year_rank NOT BETWEEN 2
  AND 3;
```

-- NOT LIKE
``` sql
SELECT
  *
FROM
  tutorial.billboard_top_100_year_end
WHERE
  year = 2013
  AND "group" NOT ILIKE '%macklemore%';

-- IS NOT NULL
``` sql
SELECT
  *
FROM
  tutorial.billboard_top_100_year_end
WHERE
  year = 2013
  AND artist IS NOT NULL;
```

-- ORDER BY (데이터 필터링)
``` sql
SELECT
  *
FROM
  tutorial.billboard_top_100_year_end
ORDER BY
  artist;
```

-- ORDER BY 오름차순
``` sql
SELECT
  *
FROM
  tutorial.billboard_top_100_year_end
WHERE
  year = 2013
ORDER BY
  year_rank;
```

-- ORDER BY 내림차순
``` sql
SELECT
  *
FROM
  tutorial.billboard_top_100_year_end
WHERE
  year = 2013
ORDER BY
  year_rank DESC;
```

-- ORDER BY 오름차순, 내림차순 동시 사용 (기준 확인 필요)
``` sql
SELECT
  *
FROM
  tutorial.billboard_top_100_year_end
WHERE
  year_rank <= 3
ORDER BY
  year DESC,
  year_rank;
```

``` sql
SELECT
  *
FROM
  tutorial.billboard_top_100_year_end
WHERE
  year_rank <= 3
ORDER BY
  year_rank,
  year DESC;
```

-- 열 번호 사용 
``` sql
SELECT
  *
FROM
  tutorial.billboard_top_100_year_end
WHERE
  year_rank <= 3
ORDER BY
  2,
  1 DESC;
```
