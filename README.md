<!-- PROJECT LOGO -->
<div align="center">
  <img src="https://i.pinimg.com/originals/a7/f2/b2/a7f2b2c622726633c316b36bd1fcf064.png" alt="Logo" width="80" height="80">
  <h1>실시간 환율 계산기</h1>
  <p>
    <a href="https://currency-converter-w.netlify.app/">배포 주소 바로가기</a>
    ·
    <a href="https://devjoylee.github.io/currency-converter/">프로젝트 회고 바로가기</a>
  </p>

[![Contributors][contributors-shield]][contributors-url]

[contributors-shield]: https://img.shields.io/github/contributors/devjoylee/currency-converter.svg?style=for-the-badge
[contributors-url]: https://github.com/devjoylee/currency-converter/graphs/contributors

</div>

<!-- TABLE OF CONTENTS -->
<details align="right">
  <summary>Table of Contents</summary>
    <div><a href="#프로젝트-소개">프로젝트 소개</a></div>
    <div><a href="#기술-스택">기술 스택</a></div>
    <div><a href="#과제-구현-목록">과제 구현 목록</a></div>
    <div><a href="#CRA-구조">CRA 구조</a></div>
    <div><a href="#커밋-컨벤션">커밋 컨벤션</a></div>
    <div><a href="#과제-후기">과제 후기</a></div>
</details>

## 프로젝트 소개

> 주어진 API를 활용하여 두 종류의 환율 계산기가 각각 작동하도록 구현하는 프로젝트

### member

<table>
  <tr>
        </td>
      <td align="center">
      <a href="https://github.com/LEEHYUNHO2001"
        ><img
          src="https://avatars.githubusercontent.com/LEEHYUNHO2001"
          width="100px;"
          alt=""
        /><br /><sub><b>이현호</b></sub></a>
    <br />
    </td>
    <td align="center">
      <a href="https://github.com/hoonjoo-park"
        ><img
          src="https://avatars.githubusercontent.com/hoonjoo-park"
          width="100px;"
          alt=""
        /><br /><sub><b>박훈주</b></sub></a
      ><br />
    </td>
    <td align="center">
      <a href="https://github.com/Yoon-CH"
        ><img
          src="https://avatars.githubusercontent.com/Yoon-CH"
          width="100px;"
          alt=""
        /><br /><sub><b>윤창현</b></sub></a
      ><br />
    </td>
    <td align="center">
      <a href="https://github.com/devjoylee"
        ><img
          src="https://avatars.githubusercontent.com/devjoylee"
          width="100px;"
          alt=""
        /><br /><sub><b>이주영</b></sub></a
      ><br />
  </tr>
</table>

| 팀 구성        | 담당                              |
| -------------- | --------------------------------- |
| 이현호, 윤창현 | 선택박스 계산기 (SelectConverter) |
| 박훈주, 이주영 | 탭 계산기 (TabConverter)          |

<br/>

## 사용 기술 및 스택

<img src="https://img.shields.io/badge/html5-E34F26?style=for-the-badge&logo=html5&logoColor=white" style="display:">&nbsp;&nbsp;<img src="https://img.shields.io/badge/css-1572B6?style=for-the-badge&logo=css3&logoColor=white">&nbsp;&nbsp;<img src="https://img.shields.io/badge/javascript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black">&nbsp;&nbsp;<img src="https://img.shields.io/badge/react-61DAFB?style=for-the-badge&logo=react&logoColor=black">

<br/>

## 과제 구현 목록

### **Tab Box Converter (박훈주, 이주영)**

1. 입력값 상태 저장

![Untitled](https://user-images.githubusercontent.com/68415905/154837797-6f5b9bb5-eebb-4a9f-9b4f-8fc47bc9c815.png)

```jsx
const [inputValue, setInputValue] = useState('');
const [currency, setCurrency] = useState('USD');
```

각각 다른 state를 만들어 입력 값을 관리하도록 하였고 input의 입력값에는 10자리 이하 숫자만 입력되도록 하기위해 입력값 length가 10을 넘는 경우 return 시켰다. 그리고 `toLocaleString` 을 사용해 숫자 3자리마다 콤마(,)가 자동으로 보이도록 만들었다. ex) 1,000,000

<br/>

2. 탭 기능 구현

![Untitled](https://user-images.githubusercontent.com/68415905/154838315-42884797-688c-43c6-aab6-bc06f9b33f2a.JPG)

위 select 박스에서 선택된 단위는 아래 탭박스에 나타나지 않도록 하기위해 전체 화폐단위 값을 가져와서 `filter`로 select 박스에 선택된 값을 제외하고 탭을 다시 정렬하도록 구현했다. 활성화된 탭은 border-bottom값을 none으로 해주었다.

<br />

3. 실시간 날짜 & 환율 계산

![Untitled](https://user-images.githubusercontent.com/68415905/154838566-6341a0f4-bad8-4f66-b706-f6accb9e7488.jpg)

데이터를 성공적으로 받아오면, `DateConverter`와 `CurrencyCalculator`로 실시간 환율을 계산한다. 환율 계산할 때는, 콤마(,)때문에 string으로 변한 value값을 다시 number로 바꾸어 준다. ex) “1,000” → 1000

<br/>

## CRA 구조

```markdown
src
│
├─components
│ │  
│ └─SelectConverter  
│ │ SelectConverter.jsx
│ └─TabConverter
│ TabConverter.jsx
│
├─constants
│ index.js
│
├─pages
│ MainPage.jsx
│
├─styles
│ GlobalStyles.js
│
├─utils
│ dateConverter.js
```

<br/>

## 커밋 컨벤션

commit 메세지에 깃모지를 추가하여 어떤 작업을 수행했는지 한 눈에 확인할 수 있도록 직관성을 높였습니다.

| 깃모지 | 사용 예시               |
| ------ | ----------------------- |
| 🎉     | init                    |
| 🚚     | 디렉토리 또는 파일 이동 |
| ✨     | 기능 구현               |
| 💄     | CSS 스타일링            |
| ♻️     | 리팩토링                |
| 📝     | Readme 수정             |
| ➕     | 모듈 추가               |
| 🐛     | 버그 해결               |
| 🚑️    | 치명적인 오류 해결      |

출처 : 깃모지(http://gitmoji.dev/)

<br/>

## 과제 후기

### 이주영 🎗

이번 과제를 통해 git으로 pull request를 하며 협업하는 방식을 익힐 수 있었습니다. 이외에도 정해진 팀원과 함께한 짝 프로그래밍을 통해 몰랐던 부분이나 막히는 부분을 같이 고민하고 해결할 수 있었습니다.

### 이현호 😎

라이브 코딩을 하다보니 긴장도 되었지만, 막히는 부분에서 함께 고민하며 나아가는 모습을 보고 페어 프로그래밍의 중요성을 알게되었습니다. 그리고 제가 잘 아는 부분에 대해서 설명하면서 프로젝트를 설계하는 것으로 기초를 다시 다지게 되는 경험이 되었습니다.

### 윤창현 ✨

명확한 업무분담과 빠르고 정확한 협업과 소통으로 프로젝트를 완성 하였고, 한걸음 더 발전할 수 있었던 좋은 시간이었습니다.

### 박훈주 🎅

사실 항상 독학을 하며 코딩을 해왔었기에 협업에 익숙하지 않았었습니다. 하지만 팀원들의 도움으로 원활하게 협업하는 방식을 배울 수 있었고, 생각보다 코딩을 할 때 고려해야 할 것들이 많음을 새삼 깨달았습니다.

<p align="right">(<a href="#top">back to top</a>)</p>
