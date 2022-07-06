# Goodbye-COVID-19-APP
시도별 확진자 수를 파이 차트로 볼 수 있는 앱 <br>
<br>
## 기능 상세
시도별 신규 확진자 수가 파이 차트로 표시되어야 합니다<br>
도시 항목을 선택하면 상세 현황을 볼 수 있는 화면으로 이동되어야 합니다<br>
<br>
## 활용 기술
-굿바이 코로나 19 API<br>
-Alamofire (http 통신)<br>
-Cocoapods (외부 라이브러리 사용)<br>
<br>
## Alamofire
Alamofire는 swift 기반의 http 네트워킹 라이브러리입니다<br>
url 세션에 기반한 라이브러리로<br>
네트워킹 작업을 단순화하고 네트워킹을 위한 다양한 메소드와 JSON 파싱 등을 제공한다<br>
-특징<br>
연결 가능한 request response 메소드를 제공<br>
URL JSon형태의 파라미터 encoding 지원<br>
또 파일 데이터 스트링 multipart form 데이터 등 업로드 기능을 제공하고
http response검증과 광범위한 단위 테스트 및 통합 테스트를 보장한다<br>
<br>
사실 Alamofire 대신 애플에서 기본적으로 제공하는 URLSession을 사용해 http 통신이 가능하다<br>
그러므로 불구하고 많은 사람들이 Alamofire를 사용하는 이유는 Alamofire는 코드의 간소화 및 가독성 측면에서 도움을 주고 여러 기능을 직접 구현하지 않아도 쉽게 사용할 수 있기 때문이다.<br>
urlsession은 호출할 API의 URL을 생성하고 QueryParameter가 있다면 URL에 매핑시켜주는 코드를 작성해야 하지만, Alamofire는 요청을 생성할 때, 메소드 파라미터에 URL과 파라미터를 넘겨주면 내부애서 자동으로 매핑시켜준다<br>
유효성 검사 같은 경우에도 URL세션의 response 객체를 HTTPURLResponse로 다운캐스팅하여 Status property에 접근해 200 번대인지 확인하는 코드를 직접 작성해야 하지만<br>
Alamofire는 Validate메소드만 호출하면, 정상 status 코드 범위(200번대)만 허용하게 만들어줄 수 있다.<br>
<br>
## Alamofire 사용방법
먼저 requset 메소드를 이용하여 http 통신 요철을 할 수 있다.<br>
메소드 파라미터로 URL과 http 메소드 파라미터 등 요청에 필요한 정보를 쉽게 설정할 수 있다<br>
Alamofire는 http 메소드 또한 지원을 한다.<br>
대표적인 http메소드는 get, post, put, delete가 정의되어 있다<br>
요청을 만들 때, request 메소드 파라미터에 http 메소드를 전달할 수 있다.<br>
Alamofire에선 요청에 대한 응답을 response 메소드를 이용해서 핸들링한다<br>
응답이 완료되면 completion 핸들러가 호출된다<br>
<br>
AF.request("http://httpbin.org.get").responseJSON{ response in debugPrint(response)}<br>
reponse메소드는 다음과 같이 request 메소드와 chaining하여 사용된다.<br>
<br>
 
