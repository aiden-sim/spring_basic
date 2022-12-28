## 스프링 기초 정리
- `@ResponseBody`를 사용하면 뷰 리졸버 viewResolver 를 사용하지 않음
  - HTML Body에 데이터를 직접 넣게다는 의미 
  - ![image](https://user-images.githubusercontent.com/7076334/209816047-b6a00dd6-a7d8-42cf-8262-71d844ce7d3f.png)
    - 기본 문자처리: StringHttpMessageConverter
    - 기본 객체처리: MappingJackson2HttpMessageConverter

  - 클라이언트의 HTTP Accept 해더와 서버의 컨트롤러 반환 타입 정보 둘을 조합해서 HttpMessageConverter 가 선택된다.

- `@Autowired` 가 있으면 스프링이 연관된 객체를 스프링 컨테이너에서 찾아서 넣어준다. (DI)

- 스프링 빈을 등록하는 2가지 방법
  - 컴포넌트 스캔과 자동 의존관계 설정
    - `@Component`를 사용하면 스프링 빈으로 자동 등록됨
    - `@Controller`, `@Service`, `@Repository` annotation 내부에 `@Component` 설정되어 있음 
  - 자바 코드로 직접 스프링 빈 등록하기

- 자바 코드로 직접 스프링 빈 등록하는 형태
```
@Configuration
public class SpringConfig {
    @Bean
    public MemberService memberService() {
        return new MemberService(memberRepository());
    }
    @Bean
    public MemberRepository memberRepository() {
        return new MemoryMemberRepository();
    }
}
```
  - 이렇게 사용하면 Service나 Repository 부분을 수정하지 않고 설정만 변경해서 주입대상을 변경시킬 수 있다.


- 기본적으로 `@SpringBootApplication` 내부에 있는 `@ComponentScan`을 통해 하위 패키지를 찾아서 자동으로 스프링 빈으로 등록시킨다.

- `@Autowired` 의 setter 주입 방식은 public 하게 제공되기 때문에 중간에 변경될 소지가 있어 권장하지 않는다.

