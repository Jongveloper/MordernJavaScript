# Hello, world!

### script 태그
`<script>` 태그를 이용하면 자바스크립트 프로그램을 HTML 문서 대부분의 위치에 삽입할 수 있습니다.
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
</head>
<body>
  <p>스크립트 전</p>
  
  <script>
    alert('Hello, world!');
  </script>

  <p>스크립트 후</p>
</body>
</html>
```
`<script>`태그엔 자바스크립트 코드가 들어갑니다. 브라우저는 이 태그를 만나면 안의 코드를 자동으로
처리합니다.
### 모던 마크업
`<script>` 태그엔 몇가지 속성(attribute)이 있습니다.
요즘엔 잘 사용하지 않습니다.
#### 속성
`type` 속성: `<scripit type=...>`
HTML4에선 스크립트에 `type`을 명시하는 것이 필수였습니다.
따라서 `type="text/javascript"`속성이 붙은 스크립트를 어렵지 않게 찾을 수 있었습니다.
`language` 속성: `<script language=...>`
이 속성은 현재 사용하고 있는 스크립트 언어를 나타냅니다.
지금은 자바스크립트가 기본 언어이므로 더는 사용할 필요가 없습니다.

### 외부 스크립트
자바스크립트 코드의 양이 많은 경우엔, 파일로 소분하여 저장할 수 있습니다.
이렇게 분해해 놓은 각 파일은 `src`속성을 사용해 `HTML`에 삽입합니다.
```html
<script src="/path/to/script.js"></script>
```
여기서 `/path/to/script.js` 라는 사이트의 루트에서부터 파일이 위치한 절대 경로를 나타냅니다.
현재 페이지에서의 상대 경로를 사용하는 것도 가능합니다.
같은 폴더 내에 있는 파일인 `script.js`를 `src="script.js"`로 참조하는 것처럼 말이죠.
복수의 스크립트를 HTML에 삽입하고 싶다면 스크립트 태그를 여러 개 사용하면 됩니다.

```html
<script src="js/script1.js"></script>
<script src="js/script2.js"></script>
```
HTML 안에 직접 스크립트를 작성하는 방식은 스크립트가 아주 간단할 때만 사용합니다.
스크립트가 길어지면 별개의 분리된 파일로 만들어 저장하는 것이 좋습니다.

여러 페이지에서 동일한 스크립트를 사용하는 경우, 브라우저는 페이지가 바뀔 때마다
스크립트를 새로 받지 않고 캐시로부터 스크립트를 가져와 사용하기 때문에
트래픽이 절약되고 웹페이지의 실제 속도가 빨라집니다.

#### `src`속성이 있으면 태그 내부의 코드는 무시합니다.
`<script>` 태그는 `src`속성과 내부 코드를 동시에 가지지 못합니다.
다음 코드는 실행되지 않습니다.
```html
<script src="file.js">
  alert(1); // src 속성이 사용되었으므로 이 코드는 무시됩니다.
</script>
```
따라서, `<script src="..">`로 외부 파일을 연결할지 아니면 `<script>` 태그 내에 코드를 작성할지를
선택해야 합니다.
위의 예시는 스크립트 두 개로 분리하면 정상 작동합니다.
```html
<script src="file.js"></script>
<script>
  alert(1);
</script>
``` 