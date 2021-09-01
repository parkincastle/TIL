# 템플릿 엔진 
템플릿 양식과 특정 데이터 모델에 따른 입력 자료를 합성해서, 결과 문서를 출력하는 소프트웨어또는 컴포넌트이다.

<br>



## 템플릿 엔진의 종류

<div align = "center">
    <img src = "../img/templateEngine.png" width = "70%">
</div>

<br>

### 레이아웃 템플릿 엔진 vs 텍스트 템플릿 엔진

<br>

레이아웃 템플릿 엔진
    - 중복되는 Include 코드를 사용하지 않고도 지정된 페이지 레이아웃에 따라 페이지 타일을 조합하여 완전한 페이지로 만들어준다.
    - EX) Apache Tiles, Sitemesh 등

<br>

텍스트 테플릿 엔진
    - 템플릿 양식에 적절한 특정 데이터를 넣어 결과 문서를 출력한다.
    - EX) Freemarker, Thymeleaf, JSP(Java Server Pages) 등

<br>

### 서버 사이드 템플릿 엔진 vs 클라이언트 사이드 템플릿 엔진

Server Side Template Engine
    - 서버에서 DB 혹은 API에서 가뎌온 데이터를 미리 정의된 Template에 넣고 html을 그려서 클라이언트에 전달해주는 역할을 한다.
    - HTML 코드에서 고정적으로 사용되는 부분은 템플릿으로 만들어두고 동적으로 생성되는 부분만 템플릿 특정 장소에 끼워넣는 방식으로 동작할 수 있도록 해준다.
    - 과정
      - 1. 클라이언트의 요청을 받는다
      - 2. 필요한 데이터(DB나 API)에서 가져온다.
      - 3. 미리 정의된 Template에 해당 데이터를 적절하게 넣는다.
      - 4. 서버에서 HTML(데이터가 변경된 Template)을 그린다.
      - 5. 해당 HTML을 클라이언트에 전달한다.

<br>

Client Side Template Engine
    - html 형태로 코드를 작성할 수 있으며, 동적으로 DOM을 그리게 해주는 역할을 한다.
    - 데이터 받아서 DOM 객체에 동저긍로 그려주는 프로세스를 담당한다.
    - 과정
      - 1. 클라이언트 에서 공통적인 프레임을 미리 template으로 만든다.
      - 2. 서버에서 필요한 데이터를 받는다.
      - 3. 데이터를 template을 적절한 위치에 replace하고 DOM 객체에 동적으로 그려준다.