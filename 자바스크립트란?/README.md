# 자바스크립트란?
### 정의
자바스크립트는 **웹 페이지에 생동감을 불어 넣기 위해** 만들어진 프로그래밍 언어입니다.

자바스크립트로 작성한 프로그램을 script라고 부르고 
스크립트는 웹페이지의 HTML 안에 작성할 수 있는데, 웹 페이지를 불러올 때 스크립트가 자동으로 실행됩니다.

자바스크립트는 브라우저뿐만 아니라 서버에서도 실행할 수 있습니다.
이 외에도 [자바스크립트 엔진](#자바스크립트-엔진)이라 불리는 특별한 프로그램이 들어 있는 모든 디바이스에서도 동작합니다.

브라우저엔 **자바스크립트 가상 머신** 이라 불리는 엔진이 내장되어 있습니다.

### 엔진의 기본 동작 원리
1. 엔진이 스크립트를 읽습니다 (파싱)
2. 읽어 들인 스크립트를 기계어로 전환합니다 (컴파일)
3. 기계어로 전환된 코드가 실행됩니다. 기계어로 전환되었기 때문에 실행 속도가 빠릅니다.

엔진은 프로세스 각 단계마다 최적화를 진행합니다.
심지어 컴파일이 끝나고 실행 중인 코드를 감시하면서, 이 코드로 흘러가는 데이터를 분석하고,
분석 결과를 토대로 기계어로 전환된 코드를 다시 최적화하기도 합니다.
이런 과정을 거치면 스크립트 실행 속도는 더욱 더 빨라집니다.

### 브라우저에서 할 수 있는 일
웹페이지 조작, 클라이언트와 서버의 상호작용에 관한 모든 일을 할 수 있습니다.
- 페이지에 새로운 HTML을 추가하거나 기존 HTML, 혹은 스타일 수정하기
- 마우스 클릭이나 포인터의 움직임, 키보드 키 눌림 등과 같은 사용자 행동에 반응하기
- 네트워크를 통해 원격 서버에 요청을 보내거나, 파일 다운로드, 업로드하기
- 쿠키를 가져오거나 설정하기. 사용자에게 질문을 건네거나 메시지 보여주기
- 클라이언트 측에 데이터 저장하기 (웹 스토리지)

### 브라우저에서 할 수 없는 일
브라우저는 보안을 위해 자바스크립트의 기능에 제약을 걸어놓았습니다.
악성 웹페이지가 개인 정보에 접근하거나 사용자의 데이터를 손상하는 것을 막기 위해 만들어졌습니다.
- 디스크에 저장된 임의의 파일을 읽거나 쓰고, 
복사하거나 실행할 때 제약을 받을 수 있습니다.
모던 브라우저를 사용하면 `input`태그를 통해 
파일을 선택할 때와 같이 특정 상황에서만 파일 접근을 허용합니다.
- 카메라나 마이크 같은 디바이스와 상호 작용하려면 사용자의 명시적인 허가가 있어야 합니다.
- 브라우저 내 탭 창과 창은 대게 서로의 정보를 알 수 없습니다.
- 자바스크립트를 이용하면 페이지를 생성한 서버와 쉽게 정보를 주고받을 수 있지만,
타 사이트나 도메인에서 데이터를 받아오는 것은 불가능합니다.
가능하다 할지라도 원격 서버에서 명확히 승인을 해줘야합니다.

### 자바스크립트만의 강점
- HTML/css와 완전히 통합할 수 있음
- 간단한 일은 간단하게 처리할 수 있게 해줌
- 모든 주요 브라우저에서 지원하고, 기본 언어로 사용됨


### 자바스크립트 엔진
자바스크립트 엔진은 자바스크립트 코드를 실행하는 소프트웨어 구성 요소입니다.
일반적으로 웹 브라우저 공급업체에서 개발하며 모든 주요 브라우저에 하나가 있습니다.
브라우저에서 자바스크립트 엔진은 DOM을 통해 렌더링 엔진과 함께 실행됩니다.
자바스크립트 엔진의 사용은 브라우저에만 국한되지 않고 
`Node.js` 및 `Deno`런타임 시스템의 핵심 구성요소입니다.

### 출처 목록
- [자바스크립트란?](https://ko.javascript.info/intro)
- [자바스크립트 엔진 : 위키피디아](https://en.wikipedia.org/wiki/JavaScript_engine)
