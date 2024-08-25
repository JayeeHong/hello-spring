## 강의 내용 몇가지 정리 

### 정형화된 패턴
- Controller -> Service -> Repository

### 컴포넌트 스캔 & 자동 의존관계 설정
@Controller <br/>
@Service<br/>
@Repository<br/>
-> 모두 @Component 에 포함되어 있음<br/>
-> "컴포넌트 스캔" (@SpringBootApplication 하위의 컴포넌트만 스캔 대상임)

### 스프링 컨테이너 (싱글톤 패턴)
예를 들어.. <br/>
MemberController는 MemberContorller 하나만 있음<br/>
(특수한 케이스에는 싱글톤 아니게 설정 가능함)

### @Autowired
생성자에 달려있으면, 객체 생성 시점에 스프링 컨테이너에서 해당 스프링 빈을 찾아 주입함<br/>
주입 -> Injection -> DI -> 의존성 주입!

### SOLID

### OCP (Open-Closed Principle, 개방 폐쇄 원칙)
확장에는 열려있고 수정(변경)에는 닫혀 있다.<br/>
객체지향의 다형성을 활용 -> 실제 동작하는 코드는 수정하지 않아도 기능을 확장시킬 수 있다. <br/>
<br/>
예를 들어)<br/>
- interface: MemberRepository를
- MemoryMemberRepository, JdbcMemberRepository에서 구현 한다면 <br/>

SpringConfig에서<br/>
-> MemberRepository를 빈으로 등록할 때 MemoryMemberRepository 또는 JdbcMemberRepository 를 상황에 따라 설정할 수 있다. <b>(확장)</b> <br/> 
-> 실제 기능이 구현된 소스코드는 수정하지 않음! <b>(수정/변경)</b>

### @Transactional
Test 클래스에 붙으면: 하나의 test 메소드 실행 후 DB Rollback함

### 테스트용어
- 단위테스트: 메모리에 올려서 하는 test
- 통합테스트: SpringBootTest처럼 서버 올려서 하는 test<br/>

-> 단위테스트를 습관화하는 것이 좋다

### JPA
- 관계형 데이터베이스에서는 필수 기술로 보면됨
- 스프링 데이터 JPA: JPA를 편리하게 사용하게 해주는 도구(라이브러리)
- interface 생성 시.. extends JPARepository
  -> 스프링 데이터 JPA가 Bean에 등록함<br/>

- 동적쿼리: QueryDsl
- native query: JPA에서 제공 또는 Jdbctemplate도 사용<br/>

참고) build.gradle 설정: JPA 등록하면 jdbc 포함함<br/><br/>

### AOP (공통관심사항 vs 핵심관심사항)
- 핵심관심사항: 핵심로직
- 공통관심사항: 메소드걸리는시간 측정 등 핵심로직을 제외하고 모든 메소드에 공통으로 들어갈 로직 <br/>
  -> AOP 사용 가능 <br/>

- AOP: Aspect Oriented Programming (관점지향 프로그래밍) <br/>
  -> 공통 관심사와 핵심관심사를 분리시킨다 <br/>
  -> 스프링의 DI 기술 중 하나 <br/>
  -> Spring: @Aspect 사용 <br/>
  참고) @Aspect: @ComponentScan 지정하거나 SpringConfig 쪽에 Bean을 명시적으로 등록해도 된다. <br/>

- AOP 적용시
  1. 스프링 컨테이너가 AOP가 적용된 클래스의 프록시를 생성하여 적용한다.
  2. 프록시가 실제 클래스를 호출한다 (Controller, Service... 등)

  
