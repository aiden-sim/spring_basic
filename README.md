## 스프링 기초 정리
- `@ResponseBody`를 사용하면 뷰 리졸버 viewResolver 를 사용하지 않음
  - HTML Body에 데이터를 직접 넣게다는 의미 
  - ![image](https://user-images.githubusercontent.com/7076334/209816047-b6a00dd6-a7d8-42cf-8262-71d844ce7d3f.png)
    - 기본 문자처리: StringHttpMessageConverter
    - 기본 객체처리: MappingJackson2HttpMessageConverter

  - 클라이언트의 HTTP Accept 해더와 서버의 컨트롤러 반환 타입 정보 둘을 조합해서 HttpMessageConverter 가 선택된다.

