# dom function
HTML 파싱을 CSS 셀렉터로 간편히 사용할 수 있는 함수입니다

## Installation
아래 두가지 방법중 하나를 선택하여 설치하세요. 먼저 [git](https://git-scm.com/download/win)이 설치되어 있어야 합니다.

오토핫키 스크립트로 설치하는 방법:
```ahk
; 표준 라이브러리에 설치
RunWait git clone https://github.com/neovis22/dom.git, % a_ahkPath "\..\Lib"

; 로컬 라이브러리에 설치
RunWait git clone https://github.com/neovis22/dom.git Lib/dom
```

사용할 스크립트에 아래 코드를 추가하세요.
```ahk
#Include <dom\dom>
```

## Usage

#### 기본 사용법
```ahk
dom := dom(html)
```
생성된 `dom`은 엘리먼트로 취급되며 `DOMElement` 클래스로 랩핑되고 엘리먼트의 메소드 및 속성을 사용할 수 있습니다.

`html`내의 스크립트 코드는 자동실행을 방지하기 위해 빈 스크립트로 치환됩니다. 스크립트 코드를 유지하기 위해서는 `removeScripts`를 `false`로 설정하세요.

#### 셀렉터를 이용한 엘리먼트를 탐색
```ahk
html := "
(join ltrim
<div class='list-a'>
    <ul class='items'>
        <li>Apple</li>
        <li>Banana</li>
        <li>Orange</li>
    </ul>
</div>
<div class='list-b'>
    <ul class='items'>
        <li>Grape</li>
        <li>Lemon</li>
    </ul>
</div>
)"

dom := dom(html)

for i, el in dom.querySelectorAll(".list-b ul.items li")
    out .= (a_index-1 ? "," : "") el.innerText
MsgBox % out ; Grape,Lemon
```
`NodeList`는 `DOMElements` 클래스로 랩핑되며 `for`문 사용을 지원합니다.

항목에 접근하거나 열거시 자바스크립트와 통일성을 위해 인덱스는 `1`이 아닌 `0`부터 시작됩니다.

## Functions
- `dom(html, removeScripts=true)`

## Contact
[카카오톡 오픈 프로필](https://open.kakao.com/me/neovis)
