<7.4>

maven dependency 이용해서 library 직접 add 안하게 하기
spring

- 라이브러리 평가 양식 - 
용량, 퍼포먼스, 가독성, 사용자 깃헙통계, 사용가능 언어, 결과물 형태, 오픈소스여부, 결제여부, 버전

- 네이버 캘린더 시간표 마크업 소스 확인 해서 로컬에서 바꿔보기
- spring 학습
- 최고 목표는 페이지의 일정 부분만 추출해서 프린트하게 하기

<7.5>
html to xhtml converter apply
플래시 동작 원리
- Jtidy?
목표 : 1. 네이버 캘린더 페이지 소스 export하여 로컬에서 테스트 == export완료/ htmlparser로 테스트시 한글, css 등 깨지고 원본에서 변형되어 변환됨
2. http url통한 변환 기능 구현
3. 간단한 웹페이지 작성 및 깃헙 공유
4. 일정부분 (이미지 파일이나 텍스트 등) 만 가져와서 변환 시켜보기( changing calendar css rules)

- 문제 -
0. 서버사이드에서 이미지로 변환하여 출력하게끔하기 - 이미지로 변환 라이브러리
1. 깔끔한 a4사이즈의 pdf로 변환하려면 결국 소스파일을 수정해야하는지? - 일정부분만 추출하여 렌더링하도록?
2. 시간표 기능이 출력버튼 누르고 팝업되는 뷰에서 볼 수 있는지?
3. google calendar 역시 pdf저장시 원본을 수정하여 변환시킴
4. wkhtmltopdf의 경우 jar file 존재하지 않아 web app에 integration 불가

발견
1. css2의 경우 적용가능/ css3에서 webkit, box-resizing등 브라우저에 dependent한 요소들은 인식 불가(@meaida rule, transition, -moz ..)

==Spring==

DI : dependency injection
dependency? : object와 object간의 의존성 - A라는 클래스에서 B라는 클래스의 메소드를 불러와 실행하게 될때 그것을 의존한다

만약 B클래스의 메소드가 바뀌면? -> A안에서도 마찬가지로 변경해줘야함 다수의 클래스가 그럴시 직접 변경 힘들어짐

따라서 유지보수의 어려움을 덜기위해 DI이용 - 3자(Service)가 만들어준 의존객체를 각 클래스에 뿌려주어 변경의 유연성 제공

service역할을 하는 설정파일(XML - applicationContext.xml)을 만들어 각 클래스에서 의존객체들을 주입받음(beans태그 안 객체관리 컨테이너에 설정)

Beans 저장위한 클래스파일에서 객체 생성 방법 : ServiceDao객체 생성

Bean? : 자주 사용하는 객체를 Singleton 객체(인스턴스가 하나뿐인 객체)로 생성해놓고 어디서든 불러서 쓸 수 있는 것을 Spring 에서 Bean 이라는 이름을 붙인 것
        , IoC(inversion of control)방식으로 관리하는 object임 = managed object

