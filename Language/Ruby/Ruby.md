# Ruby 란?

<div align = "center">
    <img src = "../../img/Ruby2.png" width = "30%">
</div>

<br>

Ruby는 일본 개발자 유키히로 마츠모토가 개발한 **스크립트 언어이자 순수한 객체 지향 프로그래밍 언어**이다. 
Ruby는 사람에게 매우 친숙한 언어를 지향하기 때문에 원하는 부분을 자유롭게 바꿀수 있는 유연성과 함께 블록이나 믹스인과 같이 다른 언어를 가지고 있지 않은 다양한 매력을 보유하고 있다.

## Ruby의 특징

 - **자유로운 형식**
  
    : Ruby는 다른 언어에 비해서 들여 쓰기가 크게 중요하지 않은 언어이다. 때문에 모든 행과 열에서 프로그램을

 - **대소문자 구분**

    : Ruby에서 들여 쓰기는 중요하지 않지만 대문자와 소문자를 꼭 구분해야 한다. 예를 들어 'end'와 'END'는 완전히 다른 키워드를 의미한다.

 - **주석**

    : Ruby에서 '#' 부호 뒤에 작성된 내용은 한 줄 단워로 주석 처리된다. 큰 주석 블록을 만들기 위해서는 '=begin'과 '=end'를 사용한다.

    예)
    ```Ruby
    #한 줄 주석입니다.
    puts 'A'	#A를 출력합니다.
    puts 'B'	#B를 출력합니다. 
    =begin
    여러분이 Ruby에서
    여러 줄의 주석을 작성할 때는
    다음과 같이 처리하면 됩니다!
    =end
    puts 'C'
    ```

 - 문장 구분 기호 

    : 일반적인 프로그래밍 언어는 하나의 구문이 끝날 때마다 세미콜론(;)을 붙여야 한다. 한 줄 코드의 종결을 의미한다. 하지만 Ruby는 줄바꿈으로 코드의 종결을 구분한다. 만약 한 줄에 여러 구문을 사용하면 세미콜론으로 구분한다.

    ```Ruby
    a = 1
    puts a
    b = 2; puts b;
    ```

 - 키워드
    : Ruby에는 41개의 키워드가 있다. 이 키워드들은 Ruby의 문법 체계를 구성하는 중요한 요소이기 때문에 변수의 이름이나 클래스의 이름으로 사용할 수 없다.

   | _ENCODING_ | _LINE_ | _FIE | BEGIN | END |
   | ---- | ---- | ---- | ---- | ---- |
   | alias | and | bdgin | break | case |
   | class | def | defined | do | else |
   | elsif | end | ensure | false| for | 
   | if | in | module | next | nil|
   | not | or | redo | rescue| retry |
   | return | self | super | then | true |
   | undef | unless | until | when | while |
   | yield |