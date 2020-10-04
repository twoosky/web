# 1. HTTP protocal 
## HTTP(Hypertext Transfer Protocol)
인터넷상에서 데이터를 주고 받기 위한 서버/클라이언트 모델을 따르는 프로토콜이다. 애플리케이션 레벨의 프로토콜로 TCP/IP위에서 작동한다.
  * 비연결성(Connectionless)
    * 요청을 받은 서버가 응답하게 되면 소켓을 유지하지 않고 연결을 disconnect한다.
    * 연결을 유지하게 되면 리소스가 계속 사용되고 리소스가 부족하면 다른 사용자가 이용하지 못하기 때문에 결과적으로 더 많은 연결을 위해 비연결 지향으로 설계
    
  * 무상태(Stateless)
    * 클라이언트가 사용자 인증을 하더라도 상태가 유지되지 않기 때문에 Cookie(쿠키) 혹은 Session(세션)을 이용해 인증 등을 해결하기도 한다.
## TCP/IP
TCP규약과 IP규약을 합친 웹 상에서만 사용하는 규칙
  * TCP
    * 데이터 전달을 관리하는 규칙이다. 
    * TCP는 패킷을 조립하고, 손실된 패킷을 확인하고, 재전송하도록 요청하는 기능을 한다.
    
      * 패킷 : 데이터를 일정한 크기로 자른 단위로 인터넷에서 정보를 전달하는 단위이다. 
    
  * IP
    * 인터넷에서 컴퓨터의 위치를 찾아서 데이터를 전송하기 위해 지켜야 할 규약이다.
    * IP는 4개의 숫자로 구성되며 숫자의 크기에 따라 IPv4, IPv6으로 나뉜다.
    
  * TCP/IP 4계층
    * OSI(Open Systems Interconnections)7계층은 시스템들의 연결을 위한 모델입니다. TCP/IP 4계층은 이를 웹 서비스에 맞게 단순화시킨 모델입니다.
    
    <img src="https://miro.medium.com/max/875/1*fXqgq7Gvx_5vUUAV6EIi4g.png" width="400px" height="250px"></img><br/>
    * 응용 계층
      * HTTP, FTP, Telnet, SMTP 등 네트워크를 사용하는 응용프로그램으로 이뤄집니다.
    * 전송 계층
      * TCP, UDP 등 시스템을 연결하고 데이터를 전송하는 역할을 합니다.
    * 인터넷 계층
      * ICMP, IGMP, IP등 데이터를 정의하고 데이터의 경로를 라우팅합니다.
    * 물리 계층
      * Ethernet, ATM등 네트워크 하드웨어를 의미합니다.
      
  * TCP/IP 데이터 통신 순서
  
    <img src="https://miro.medium.com/max/823/1*qK2A5ivG6Z9IABU6rgu85g.png" width="400px" height="550px"></img><br/>
    * 클라이언트로부터 특정 주소 요청이 들어오면 DNS 상에서 IP주소를 받아옵니다.
    * HTTP 계층에서 HTTP 메시지를 작성합니다.
    * TCP 계층에서 HTTP 메시지를 패킷으로 분해합니다.
    * IP계층에서 전송위치를 확인하고 네트워크를 통하여 전송합니다.
    * 이후는 위의 과정의 역순으로 진행하여 처리합니다. 
## HTTP HEADER/BODY
* HTTP Header
  * 저장되거나 전송되는 데이터 블록의 맨 앞에 위치한 데이터를 가리킵니다.
  * 특정 프로토콜의 기능을 제공하기 위한 정보를 담고 있습니다.
  * 헤더의 뒤에 이어지는 데이터는 페이로드 혹은 바디로 불립니다.
  * HTTP 헤더는 클라이언트와 서버가 요청 또는 응답으로 부가적인 정보를 전송할 수 있도록 해줍니다.

* General header
  * 요청 및 응답 메시지 모두에서 사용되지만 컨텐츠 자체에는 적용되지 않는 헤더
  * 사용되고 있는 Context에 따라 response, request 헤더로 사용됩니다. 그러나 entity헤더는 아닙니다.
  
    * Date : 현재시간
    * Pragma : 캐시제어(no-cahce), HTTP/1.0에서 쓰던 것으로 HTTP/1.1에서는 Cache-Control이 쓰인다.
    * Cache-Control : 캐시제어
    * Upgrade : 프로토콜을 업그레이드 HTTP/2.0
    * Via : 이용할 프록시의 이름, 프로토콜 버전, 호스트명
    * Connection : 전송이 완료된 후 연결을 유지할지 말지 나타냅니다. HTTP/1.1의 경우 keep-alive가 default입니다.
    
* Request header
  * HTTP 요청에서 사용되지만 메시지의 컨텐츠와는 관련이 없는 헤더입니다.
  * Accept, Accept-*, If-* 와 같은 request 헤더 들은 조건부 요청 수행을 허용합니다.
  * Cookie, User-Agent, Referer와 같은 다른 것들은 컨텍스트를 정확히 나타내어 서버가 응답에 맞출 수 있게 합니다.
  
    * Host : 서버의 도메인명과 서버의 포트를 지정합니다.
    * User-Agent : 클라이언트 정보를 포함합니다(예:브라우저 정보)
    * Referer : 현재 주소로 접근할 수 있었던 이전 주소의 정보를 포함합니다.
    * Accept : 클라이언트가 이해할 수있는 미디어 타입에 대한 정보를 포함합니다.
    * Accept-Charset : 클라이언트가 이해할 수 있는 캐릭터 셋에 대한 정보를 포함합니다.
    * Accept-Language : 클라이언트가 어떤 언어를 이해할 수 있는지, 그리고 locale중 어떤 것이 선호되는지에 대한 정보를 포함합니다.
    * Accept-Encoding : 클라이언트가 이해 가능한 컨텐츠 인코딩 방법에 대한 정보를 포함합니다.
    * Authorization : 클라이언트의 자격증명을 포함합니다.
    * Origin : fetch를 요청한 원래의 주소의 정보를 포함합니다. 경로 정보는 포함하지 않습니다.
    * Cookie : Set-Cookie헤더와 함께 서버에 의해 이전에 전송되어 저장된 쿠키를 포함합니다.
    
* Response header
  * HTTP 응답에서 사용될 수 있는 헤더입니다. 컨텐츠와는 관련이 없습니다. 
  * Age, Location, Server와 같은 response 헤더는 더 상세한 응답의 컨텍스트를 제공하기 위해 사용됩니다.
  
    * Transfer-Encoding : body 내용 자체 압축 방식 지정
    * Expires : 응답의 유효기간을 설정합니다.
    * Last-Modified : 서버가 알고 있는 가장 마지막 수정 된 날짜와 시각을 표시합니다.
    * ETag : 특정 리소스를 식별하는 식별자. 컨텐츠가 변경되었는지 알 수 있습니다.
    * Set-Cookie : 서버에서 사용자 브라우저에 쿠키를 전송하기 위해 사용됩니다.
    * Location : 리다이렉트 될 주소에 대한 정보를 포함합니다. Status Code가 3xx 혹은 201일 경우에 볼 수 있다.
    * Server : 요청을 처리하는 서버의 소프트웨어 정보를 포함합니다.
    * Age : Max-Age의 시간 내에서 얼마나 흘렀는지에 대한 정보를 포함합니다.
    * WWW-Authenticate : 리소스에 접근하기 위해 사용되어야 하는 메소드에 대한 정보를 포함합니다. 401 Unauthorized 응답과 함께 전송됩니다.
    
* Entity header
  * 메시지 바디의 컨텐츠를 나타내는 헤더입니다.
  * TTP Request, Response 모두에서 사용됩니다.
    
    * Content-Encoding : 미디어 타입을 압축하기 위해서 사용됩니다. 클라이언트는 본문을 압축한 방식을 알 수 있습니다.
    * Content-Type : 본문의 미디어 타입을 나타내기위해 사용됩니다.
    * Content-Length : 본문의 길이를 나타냅니다.
    * Content-Language : 본문이 대상으로 하는 언어를 의미합니다.
    * Content-Location : 컨텐츠에 접근할 수 있는 위치를 나타냅니다.
    * Allow : 리소스가 지원하는 메소드의 집합을 의미합니다.
    
* HTTP Body(Request)
  * 단일-리소스 본문(single-resource bodies)
    * 헤더 두 개(Content-Type와 Content-Length)로 정의된 단일 파일로 구성됩니다.
    
  * 다중-리소스 본문(multiple-resource bodies)
    * 멀티파트 본문으로 구성되는 다중 리소스 본문에서는 파트마다 다른 정보를 지니게 됩니다. 보통 HTML 폼과 관련이 있습니다.

* HTTP Body(Response)
  * 이미 길이가 알려진 단일 파일로 구성된 단일-리소스 본문 
    * 헤더 두개(Content-Type와 Content-Length)로 정의 합니다.
    
  * 길이를 모르는 단일 파일로 구성된 단일-리소스 본문 
    * Transfer-Encoding가 chunked로 설정되어 있으며, 파일은 청크로 나뉘어 인코딩 되어 있습니다.
    
  * 서로 다른 정보를 담고 있는 멀티파트로 이루어진 다중 리소스 본문 
    * 이 경우는 상대적으로 위의 두 경우에 비해 보기 힘듭니다.
    
## Method
* 요청하는 데이터에 특정 동작을 수행하고 싶을 경우 사용.
  * GET : 존재하는 자원에 대한 요청
  * POST : 새로운 자원을 생성
  * PUT : 존재하는 자원에 대한 변경
  * DELETE : 존재하는 자원에 대한 삭제
  * HEAD : 서버 헤더 정보를 획득. GET과 비슷하나 Response Body를 반환하지 않음
  * OPTIONS : 서버 옵션들을 확인하기 위한 요청. CORS에서 사용
  
## URL
* Uniform Resouce Locators의 약자로 해당 정보 자원의 위치와 종류를 파악해야 할 때 사용하는 일련의 규칙

<img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FwH3Ot%2FbtqwixsxiB9%2FSphtWtrhOOtMdgi3rXzzR0%2Fimg.png" width="650px" height="120px"></img><br/>

* Schem
  * 리소스에 어떻게 접근하는지 알려주는 중요한 정보
  * URL을 해석하는 어플리케이션이 어떤 프로토콜을 사용하여 리소스를 요청해야 하는지 알려준다.
  * 첫번째 구분자로 :를 사용한다.
  * 스킴명은 대소문자를 가리지 않는다.
  
* Host
  * 어플리케이션이 인터넷에 있는 리소스를 찾으려면 리소스를 호스팅하고 있는 장비와 장비 내에서 리소스에 접근할 수 있는 서버가 어디에 있는지 알아야 한다. 
  * 접근하려고 하는 리소스를 가지고 있는 인터넷상의 호스트장비를 가리킨다.
  * 호스트명이나 IP주소로 제공한다.

* Port
  * 서버가 열어놓은 네트워크 포트를 가리킨다.
  * TCP 프로토콜을 사용하는 HTTP는 기본 포트가 80이다.

* Path
  * 리소스가 서버의 어디에 있는지 알려준다.
  * 계층적 파일 시스템 경로와 유사한 구조이다.
  * / 를 기준으로 경로조각으로 나뉜다.
  * 각 경로조각은 자체만으로 파라미터 컴포넌트를 가질 수 있다.
  
* Query
  * 쿼리 스트링 또는 search라고도 하며 URL에 전달할 문자열을 지정한다.
  * 쿼리 segment들로 구성되고, 이들은 &로 구분된다.
  
* Fragment
  * 리소스의 특정 부분을 가리킬 수 있도록 리소스 내 조각을 가리킬 수 있는 fragment 컴포넌트를 제공한다.
  * 보통 서버에는 fragment를 전달하진 않고, 프론트에서 특정 문단을 보여주고 싶을 때 사용한다.
  
# Web Framework
* 동적인 웹 페이지나, 웹 애플리케이션, 웹 서비스 개발 보조용으로 만들어지는 애플리케이션 프레임워크의 일종이다.
* 웹 페이지를 개발하는 과정에서 겪는 어려움을 줄이는 것이 주 목적으로 통상 데이터베이스 연동, 템플릿 형태의 표준, 세션 관리, 코드 재사용 등의 기능을 포함하고 있다.


     <img src="https://thebook.io/img/006806/8-6.jpg" width="450px" height="300px"></img><br/>

* 라우터
  * http 메서드와 URL 패턴별로 핸들러를 등록하고, 웹 요청이 들어왔을 때 적절한 핸들러로 연결해준다.

* 컨텍스트
  * 웹 요청의 처리 상태를 저장한다. 이를 통해 URL 매개변수의 값을 핸들러 내부에 전달할 수 있다.
    * URL 패턴을 /users/:id/addressses/:addresss_id로 지정하여 핸들러를 등록했을 때는 핸들러 내부에서는 user_id와 address_id의 값을 알 수 있어야 한다.
    
* 핸들러
  * URL별로 요청을 처리하는 함수

* 미들웨어
  * 대부분의 핸들러에서 공통으로 처리해야 하는 작업을 미들웨어로 만들고 웹 요청 처리시 적용시키는 것이다.
    * 에러 처리
    * 웹 요청에 대한 인증 처리
    * 웹 요청 내용 파싱
    * 로그 처리
    * 정적 파일 처리
    * 웹 요청 정보 파싱 등
    
   * 미들웨어 타입 정의
     ```
     type Middleware func(next HandlerFunc) HandlerFunc
     ```
     * Middleware는 HandlerFunc을 매개변수로 받아 새로운 HandlerFunc을 반환한다. 즉, 다음에 실행할 핸들러를 매개변수로 전달받고, 전달받은 핸들러 앞/뒤에 미들웨어 로직을 추가하여 다시 반환하는 형식이다. 
     * 체인 형태로 연결된다.
     
 * 쿠키 : 클라이언트 로컬에 저장되는 Key-Value 쌍의 작은 데이터 파일
    * 구성요소
      * 쿠키이름, 쿠키값, 만료시간, 전송할 도메인명, 전송할 경로, 보안연결 여부, HttpOnly여부
    
    * 동작방식
  
     <img src="https://miro.medium.com/max/875/1*fWfKsO9P2rReNzJM2doBhQ.png" width="400px" height="250px"></img><br/>
     
     
     1. 클라이언트가 서버에 로그인 요청을 합니다.
     2. 서버는 클라이언트의 로그인 요청의 유효성을 확인하고(아이디, 비밀번호 검사) 응답헤더에 set-cookie: user=chrisjune 를 추가하여 응답합니다.
     3. 클라이언트는 이후 서버에 요청할 때 전달받은 cookie: user=chrisjune쿠키를 자동으로 요청헤더에 추가하여 요청합니다. 헤더에 쿠키값을 자동으로 추가하여 주는데 이는 브라우저에서 처리해주는 작업입니다.
     
* 세션 : 브라우저가 종료되기 전까지 클라이언트의 요청을 유지하게 해주는 기술
  *동작방식
  
    <img src="https://miro.medium.com/max/875/1*oiHghHg3sQW5ynmMCAtPAA.png" width="400px" height="250px"></img><br/>
  
  
    1. 클라이언트가 서버에 로그인 요청을 합니다.
    2. 서버는 클라이언트의 로그인 요청의 유효성을 확인하고 unique한 id를 sessionid라는 이름으로 저장합니다.
    3. 서버가 응답할 때 응답헤더에 set-cookie: sessionid:alx2fjz를 추가하여 응답합니다.
    4. 클라이언트는 이후 서버에 요청할 때 전달받은 sessionid:a1x2fjz 쿠키를 자동으로 요청헤더에 추가하여 요청합니다.
    5. 서버에서는 요청헤더의 sessionid 값을 저장된 세션저장소에서 찾아보고 유효한지 확인후 요청을 처리하고 응답합니다.
      
* 쿠키/세션 차이점
  * 저장위치
    * 쿠키는 로컬에, 세션은 로컬과 서버에 저장된다.
  * 보안
    * 쿠키는 탈취 변조 가능, 세션은 id값만 가지고 있고 서버에도 저장되므로 상대적으로 안전하다.
  * Lifecycle
    * 쿠키는 브라우저를 종료해도 파일로 남아있지만, 세션은 브라우저 종료 시 세션 삭제
  * 속도
    * 쿠키는 파일에서 읽으므로 상대적으로 빠르고, 세션은 요청마다 서버에서 처리해야하므로 비교적 느리다.
    
## MVC
* Model, View, Controller의 약자 입니다. 하나의 애플리케이션, 프로젝트를 구성할 때 그 구성요소를 세가지의 역할로 구분한 패턴입니다. 
* 사용자가 controller를 조작하면 controller는 model을 통해서 데이터를 가져오고 그 정보를 바탕으로 View를 제어해서 사용자에게 전달하게 됩니다.


    <img src="https://mblogthumb-phinf.pstatic.net/MjAxNzAzMjVfMjUw/MDAxNDkwNDM4NzI4MTIy.4ZtITJJKJW_Nj1gKST0BhKMAzqmMaYIj9PobYJMFD4Ig.xTHT-0qyRKXsA4nZ2xKPNeCxeU2-tLIc-4oyrWq5WBgg.PNG.jhc9639/mvc_role_diagram.png?type=w800" width="700px" height="250px"></img><br/>

* Model
  * 애플리케이션의 정보, 데이터를 나타냅니다.
  * 데이터베이스, 처음의 정의하는 상수, 초기화값, 변수 등을 뜻하고 이러한 DATA, 정보들의 가공을 책임지는 컴포넌트
    * 사용자가 편집하길 원하는 모든 데이터는 가지고 있어야 한다.
    * 뷰나 컨트롤러에 대해서 어떤 정보도 알지 말아야 한다.
    * 변경이 일어나면, 변경 통지에 대한 처리방법을 구현해야만 한다.

* View
  * input 텍스트, 체크박스 항목 등과 같은 사용자 인터페이스 요소를 나타냅니다. 
  * 데이터 및 객체의 입력, 출력 담당
    * 모델이 가지고 있는 정보를 따로 저장해서는 안된다.
    * 모델이나 컨트롤러와 같이 다른 구성요소들을 몰라야 된다.
    * 변경이 일어나면 변경통지에 대한 처리방법을 구현해야만 한다.
    
* Controller
  * 데이터와 사용자인터페이스 요소들을 잇는 다리역할, '이벤트' 처리
    * 모델이나 뷰에 대해서 알고 있어야 한다.
    * 모델이나 뷰의 변경을 모니터링 해야 한다.
  

     
   
  
