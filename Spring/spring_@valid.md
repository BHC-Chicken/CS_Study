> [해당 포스팅](https://hello-judy-world.tistory.com/)에서도 내용을 확인할 수 있습니다.

> written by [judy](https://github.com/ParkJungYoon)

오늘도 평화롭게 개발하던 토끼에게 온 한 카톡!

> 🐟 : createRecordRequest에서 int말고 Integer로 해야 not null 어노테이션이 동작해요! Int는 기본값이 0이라서

엇...!

> 🐰 : 찾았다.. 😏 이번주 스터디 주제(?)

validator 공부해보자!

```java
@Schema(nullable = false)
@NotNull(message = "지출 비용을 입력해주세요.")
@Min(value = 0, message = "지출 비용 최소 값은 0입니다.")
@Max(value = 999999, message = "지출 비용 최대 값은 999999입니다.")
// private int price;
private Integer price;
```

<br>

# ✅ @Valid 사용해서 DTO 검증하기

## 1. 검증은 왜 필요할까?

컨트롤러의 중요한 역할 중 하나는 HTTP 요청이 정상인지 검증하는 것이다.

> 🤖 : 근데 클라이언트에서 잘못된 요청은 걸러주지 않아?

> 🐰 : 그럼 클라이언트를 거치지 않은 요청은 다 받아줄겨? 

클라이언트 검증은 조작할 수 있어 보안에 취약하다. 또한 서버에서도 잘못된 요청을 검증하는 로직을 필요하다.

 그리고 나는 그 중 DTO에서 데이터를 검증하는 방법을 알아보려고 한다.

## 2. Bean Validation

Bean Validation은 특정한 구현체가 아니라 Bean Validation 2.0(JSR-380)이라는 기술 표준이다.

즉, 검증 애노테이션과 여러 인터페이스의 모음이다.

### 1) 의존성 추가

우선 아래 코드로 의존성을 추가하자.

- `build.gradle`
```
implementation 'org.springframework.boot:spring-boot-starter-validation'
```

### 2) DTO에 적용하기


### 3) annotation 종류


### 4) @Valid의 검증

스프링 부트는 컨트롤러 매개변수에서 @Valid 어노테이션이 있으면 JSR 380 구현체인 Hibernate Validator를 자동으로 실행하고 Arguement를 검증한다.