Spring Annotation
==========

> @SpringBootApplication
```text
- @Configuration, @EnableAutoConfiguration, @ComponentScan 3가지의 Annotation 포함 
```

> @Component
```text
- value를 이용해 Bean의 이름을 지정
- 개발자가 직접 작성한 Class를 Bean으로 등록
```

> @ComponentScan
```text
- 자동으로 컴포넌트 클래스를 검색하고 검색된 컴포넌트 및 빈클래스를 Spring ApplicationContext에 등록하는 역할을 함 
```

> @Configuration
```text
- @Bean을 해당 클래스의 메소드에 적용할 경우 @Autowired 사용하여 Bean 주입 가능
```

> @Bean
```text
- Spring Container에 Bean을 등록
- name을 이용해 Bean의 이름을 지정
- 개발자가 직접 제어가 불가능한 외부 라이브러리등을 Bean으로 등록
```

> @Autowired
```text
- Type 에 따라 의존성 주입
- Bean 주입방식: @Autowired, setter, constructor
```

> @Resource
```text
- Name 에 따라 의존성 주입
```

> @Controller
```text
- Spring MVC에서 Controller 클래스에 사용
```

> @RestController
```text
- @Controller + @ResponseBody를 합친 Annotation으로 메소드의 반환 결과를 JSON 형태로 반환
```

> @RequestBody
```text
- HTTP 요청의 Body 내용(JSON이나 XML형식)을 자바 객체로 매핑
```

> @ResponseBody
```text
- 자바 객체를 HTTP 요청의 Body 내용(JSON이나 XML형식)으로 매핑
```

> @RequestHeader
```text
- Request의 header값 가져올 경우 사용
```

> @ResponseStatus
```text
- 요청 클라이언트에게 전달할 응답상태코드 값을 지정하며 Default로는 200 OK 응답코드를 반환
```

> @RequestParam
```text
- key value 형식으로 전달된 파라미터를 매핑
```

> @PathVariable
```text
- URL로 들어오는 값을 얻을경우 사용
```

> @RequestPart
```text
- Request로 온 MultipartFile(파일 업로드)을 바인딩
```

> @CookieValue
```text
- 쿠키 값을 파라미터로 전달 받을경우 사용

** 해당 쿠키가 존재하지 않으면 500 에러 발생 **
required: (default=true)
false를 적용하면 해당 쿠키 값이 없을 때 null 로 받음
```

> @Cacheable
```text
- 서비스의 메소드를 캐싱
```

> @CachePut
```text
- 메서드를 호출 할때마다 결과 데이터를 캐시에 적재
```

> @CacheEvict
```text
- 캐시 데이터 제거
```

> @CacheConfig
```text
- 공통의 캐시설정을 공유
```

> @CrossOrigin
```text
- CORS 보안상의 문제로 브라우저에서 리소스를 현재 origin에서 다른 곳으로의 AJAX요청을 방지
```

> @Service
```text
- 비즈니스 로직을 수행하는 Class라는 것을 나타내는 용도
```

> @Repository
```text
- DataBase에 접근하는 로직을 수행하는 Class라는 것을 나타내는 용도
```

> @Qualifier
```text
- @Autowired와 같이 쓰이며, 같은 타입의 Bean 객체가 있을 경우 사용
```

> @Value
```text
- properties에서 값을 가져와 적용할때 사용
```

> @Valid
```text
- 유효성 검증이 필요한 객체임을 지정
```

> @InitBinder
```text
- Spring Validator를 사용 시 @Valid annotation으로 검증이 필요한 객체를 가져오기 전에 수행할 method를 지정
```

> @RequestAttribute
```text
- Request에 설정되어 있는 속성 값을 가져올때 사용
```

> @ConfigurationProperties
```text
- properties 읽을 경우 사용
```

> @PostConstruct
```text
- 객체가 생성된 후 별도의 초기화 작업을 위해 실행하는 메소드를 선언
```

> @PreDestroy
```text
- 객체를 제거하기 전에 해야할 작업을 위해 실행하는 메소드를 선언
```

> @Lazy
```text
- Bean 지연로딩 지원 (Classe 가 실제로 사용될 때 로딩이 이뤄지게 하는 방법)
```

> @GetMapping
```text
- 요청받은 URI의 정보를 검색하여 응답
```

> @PostMapping
```text
- 요청된 자원을 생성(CREATE)
```

> @DeleteMapping
- 요청된 자원을 삭제(DELETE)

> @PutMapping
```text
- 요청된 자원을 수정(UPDATE)
```

> @Transactional
```text
- DB에 엑세스하는 여러 연산을 하나의 트랜잭션으로 처리하여 오류가 발생한 경우 롤백 처리
```

> @Scope
```text
- 스프링 Bean 생성 전략 변경시 사용 (Default: singleton)
```

> @Scheduled
```text
- 일정 시간에 로직을 수행할 경우 사용
```

> @ExceptionHandler(ExceptionClassName.class)
```text
- 예외를 처리하는 메소드를 정의
```

> @Target(ElementType.METHOD)
```text
- 어노테이션을 적용 할 위치 지정
  > TYPE: 클래스, 인터페이스, enum
  > FIELD: 클래스의 멤버 변수
  > METHOD: 메서드
  > PARAMETER: 파라미터
  > CONSTRUCTOR: 생성자
  > LOCAL_VARIABLE: 지역변수
  > ANNOTATION_TYPE: 어노테이션 타입
  > PACKAGE: 패키지
  > TYPE_PARAMETER: 타입 파라미터
  > TYPE_USE: 타입 사용
```

> @Retention(RetentionPolicy.RUNTIME)
```text
- 어노테이션이 적용될 범위로 어떤 시점까지 어노테이션이 영향을 미치는지 결정
  > Class: 어노테이션 작성시 기본값으로 클래스 파일에 포함되지만 JVM이 로드하지 않음
  > Runtime: 클래스 파일에 포함되고, JVM이 로드해서 리플렉션 API로 참조 가능
  > Source: 컴파일 때만 사용되고, 클래스 파일에 포함되지 않음 
```