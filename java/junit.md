# Junit

## ----- Service Test -----
### Anotation
- org.springframework.boot.test.context
```text
@SpringBootTest: 스프링 부트 통합 테스트를 제공

@ActiveProfiles: 프로파일 설정 
```

- org.springframework.transaction.annotation
```text
@Transactional: 테스트를 실행할 때 마다 트랜잭션을 시작하고, 테스트가 완료되면 트랜잭션을 강제 롤백
```

- org.springframework.test.annotation
```text
@Rollback(false): 트랜잭션을 롤백 하지 않을 경우 설정
```

- org.junit.jupiter.api
```text
@Test: 테스트 메소드

@Disable: 테스트 클래스 또는 메서드를 비활성화

@DisplayName: 테스트 클래스 또는 테스트 메서드의 이름을 정의

@RepeatedTest: 테스트 메서드의 반복횟수 설정

@ParameterizedTest: 매개변수를 받는 테스트 메소드를 작성 할때 사용

@Timeout: 테스트 실행 시간을 선언 후 초과되면 실패하도록 설정

@AfterAll: 현재 클래스의 모든 테스트 끝난후 실행, 해당 메서드는 static 이어야 함

@AfterEach: 각 테스트 메서드 이후에 실행

@BeforeAll: 현재 클래스의 모든 테스트 메서드보다 먼저 실행, 해당 메서드는 static 이어야 함

@BeforeEach: 각 테스트 메서드 전에 실행
```

## Test API
- org.junit.jupiter.api.Assertions
```text
assertAll: 여러 검증을 하나로 묶어서 테스트 할 경우 사용

assertArrayEquals: 두 배열이 같지 않을 경우 junit error 발생

assertLinesMatch: List에 있는 String값이 다를 경우 junit error 발생

assertEquals: 두 값이 일치 하지 않을 경우 junit error 발생

assertNotEqual: 두 값이 일치 할 경우 junit error 발생

assertTrue: 특정 값이 false 일때, junit 에러 발생

assertFalse: 특정 값이 true 일때, junit 에러 발생

assertThrows: 예외를 발생 시키는지 확인

assertNull: 특정 값이 null 이 아닐 경우 junit error 발생

assertNotNull: 특정 값이 not null 이 아닐 경우 junit error 발생

assertSame: 두 객체가 동일하지 않을경우 junit error 발생

assertNotSame: 두 객체가 동일 할 경우 junit error 발생

assertTimeout: 특정 시간안에 실행하는지 확인

fail: junit error 발생시킬때 사용
```

## ----- Controller Test -----

## Test API
- org.springframework.test.web.servlet.MockMvc
```text
perform(): 요청을 전송하는 역할

get(), post(), put(), delete(): HTTP 메소드

params(info): 키-값 파라미터 전달

andExpect(): 응답을 검증

status(): 상태코드
  - isOk() : 200
  - isNotFound() : 404
  - isMethodNotAllowed() : 405
  - isInternalServerError() : 500
  - is(int status) : status 상태 코드

view(): 뷰 이름을 검증

redirect(): 리다이렉트 응답을 검증

model(): 컨트롤러에서 저장한 모델 정보 검증

content(): 응답에 대한 정보를 검증

andDo(print()): 요청 및 응답 전체 메세지를 확인
```