
# frontend-2th-crackYourScreen
***
<br>
<p align="center">
  <img src = "https://github.com/woorifisa-service-dev-2nd/frontend-2th-crackYourScreen/assets/101613808/192abf21-79c3-483e-8ec5-a51844445fbe">
</p>



<br>


## 팀원 구성

> 박지호
> 안성민
> 박선주
> 박은혜





## 협업 방식


### 1. 기능 정리 :
![image](https://github.com/woorifisa-service-dev-2nd/frontend-2th-crackYourScreen/assets/101613808/8b7877c0-a2bd-46da-8ef8-6b820f5bfa34)


### 2. 역할 분담 :

> 박지호 - 배경 클릭 할 때 깨짐 효과, 더블클릭 이미지 다르게 하기, BANG 텍스트 효과
> 안성민 - 페이지 랜덤 교체, 배경 효과
> 박선주 - 마우스 포인터 변경
> 박은혜 - 초기화 버튼, 사용자 이미지 업로드, UI

<br>위와 같이 역할을 분담하여 기능을 구현하고 git을 통해 합치는 과정으로 협업하였습니다.

<br>




## 기능 시연

<br>
<br>


![총시연](https://github.com/woorifisa-service-dev-2nd/frontend-2th-crackYourScreen/assets/101613808/6d6a885c-7845-48d0-8db7-5036281e243d)

<br>
<br>



## 핵심 기능 설명 및 구현 방법



### 1.배경 이미지 변경, 페이지 랜덤 :


<p align="center">
  <img src="https://github.com/woorifisa-service-dev-2nd/frontend-2th-crackYourScreen/assets/101613808/d04810f5-5b22-4a20-81b9-078ae62504c5">
</p>

``Math.random()``으로 0에서1사이의 부동소수점 난수를 생성하고 배열의 길이를 곱한 뒤
``Math.floor``로 소수점을 제거하면 랜덤으로 0부터 배열의 길이값중 하나를 반환합니다.
선택된 이미지의 경로를 HTML 엘리먼트의 src 속성에 할당하여 해당 이미지를 표시합니다.
<br>

### 2.사용자 이미지 변경 :

<p align="center">
  <img src="https://github.com/woorifisa-service-dev-2nd/frontend-2th-crackYourScreen/assets/101613808/c35f7352-9451-4ab8-b553-7199db11ff17">
</p>

input 태그에서 사용자가 선택한 파일을 ``File`` 객체로 가져와 이미지가 맞는지 확장자 유효성 검사를 합니다.
이미지 파일이 맞으면 ``FileReader`` 객체로 파일 내용을 읽어 해당 이미지를 표시합니다.

<br>

### 3.마우스 포인터 이미지 변경 :
<p align="center">
  <img src="https://github.com/woorifisa-service-dev-2nd/frontend-2th-crackYourScreen/assets/101613808/d3790252-d8ed-4e4a-affc-e29f37cf51f8">
</p>

마우스 호버가 적용되는 DOM은 실제 HTML 태그가 보이지 않는 가상 클래스이기 때문에 ``getElementBy~()``로 객체를 불러오고 CSS ``cursor``속성을 바꾸는 구현은 어려워, ``document`` 객체 내에서 마우스를 움직이는 이벤트가 발생하면 이미지가 따라오도록 하는 방식으로 구현하였습니다.

<br>

### 4.화면 클릭하면 깨짐 효과 :
<p align="center">
  <img src="https://github.com/woorifisa-service-dev-2nd/frontend-2th-crackYourScreen/assets/101613808/3ff5d6d1-9f28-4540-b3e7-1da875ae2ea3">
</p>

#### 1. 클릭 crack 이미지 삽입
한 번 클릭시 작은 크기, 더블 클릭 시 큰 크기의 crack 이미지를 삽입합니다.


클릭한 좌표를 가져오고 좌표와 이미지 크기를 고려해 이미지가 중앙에 오도록 합니다.


```
const imageX = clickX - imageSize / 2 - 50;
const imageY = clickY - imageSize / 2 + 50; // 그림 형태에 따라 정확도를  높이기 위해 넣어준 값 '50'
```

``document.body.appendChild(image);``를 사용해 이벤트 발생시 body안에 이미지가 삽입 되게 합니다.


더블 클릭 이벤트 핸들러도 만들어 콜백 함수를 바꿔 설정합니다.

#### 2. BANG!! 텍스트 삽입

객체를 가져와 innerHTML을 활용해서 bang!!! 이라는 단어를 추가합니다.

그리고 기존 설정해뒀던 bang의 크기를 1.2배 증가시키는 작업을 합니다.

``onst newSize = (parseFloat(currentSize) * 1.2) + 'px';`` 


그 다음 원래 크기로 바꾸는 작업을 합니다. 이때 함수에 지연시간 인수를 주어 애니메이션 효과가 나타납니다.

```
setTimeout(() => {
        boomText1.style.fontSize = '50px'; // 원래 크기로 설정
}, 200);// 200ms이므로 0.2초만 커졌다가 작아진다.
```

 비슷한 방식으로 글자가 일정시간 뒤 사라지게 하고

```
 setTimeout(() => {
        boomText1.style.display = 'none'; // 글자 숨기기
    }, 1000);
    
```

이후, 다시 이벤트 발생할 때 none으로 설정했던 부분을 block으로 설정해서 글자가 다시 나타날 수 있게끔 했습니다.

``boomText1.style.display = 'block';``




## 트러블 슈팅

### 1. Git 사용법
git branch 사용법을 정확하게 알지 못하여 git을 통해 서로 작성한 부분을 합치는데 어려움이 있었습니다.

### 2. 마우스 포인터 변경
마우스 커서 이미지는 원본의 크기가 너무 크면 나타나지 않는 문제가 있었습니다.
원본 이미지를 [이미지 크기 조절 사이트] (https://www.iloveimg.com/ko/resize-image/resize-jpg) 에서 크기를 줄여 사용했습니다.


### 3. 클릭 효과가 화면 범위를 벗어나는 현상
모서리 부분에 클릭으로 화면이 깨지는 효과를 주었을 때, 깨짐효과 이미지가 배경이미지 크기를 벗어나는 문제가 발생했었습니다.
body 태그에 overflow 속성을 추가하여 배경 이미지 크기를 벗어나는 효과를 잘라내는 방식으로 해결했습니다.
```
body {
  overflow : hidden; 
}
```
### 4. 이미지 추가 기능
사용자가 업로드 버튼을 눌렀을 때 선택한 파일을 자바스크립트에서 ``File`` 객체로 받아올 수 있는데, 이 파일의 바이너리 값을 가져오는 방법을 몰라 배경화면으로 보여주는 것에 어려움이 있었습니다.
찾아보니 ``FileReader`` 객체를 통해 파일 데이터를 가져올 수 있다는 것을 알게됐고 onload 이벤트핸들러를 등록하여 해결했습니다.

### 5. 마우스커서로 설정한 이미지가 나타나지 않는 현상
기존에 css의 커서옵션으로 이미지를 부여하고 있었습니다. 해당 방식에서 브라우저의 우측과 하단 영역의 끝부분으로 마우스를 이동시키면 이미지가 기본 커서로 변경되는 문제가 있었습니다.
이를 해결하기 위해 커서로 사용될 이미지태그를 추가하여 mousemove 이벤트가 발생할 때 이미지를 마우스의 위치로 이동시켜주어 위 문제를 해결하였습니다. 추가로 마우스가 브라우저 영역 바깥으로 벗어날 시 이미지가 사라질 수 있도록 mouseleave 이벤트가 발생했을 때 이미지를 비활성화 하였습니다.

### 6. 버튼 클릭 시에도 효과가 나타나는 현상
리셋 버튼을 눌렀을 때 화면이 초기화 되어도 리셋버튼을 클릭했을 때 효과 때문에 화면이 완전히 깨끗해지지 않는 문제가 있었습니다.
`event.target.id === 버튼 객체의 id` 조건문을 통해 이벤트 콜백 함수를 동작없이 리턴시키도록 if 문을 활용했습니다.


<br>


## 회고


> **박지호:** 
처음으로 웹 디자인 협업을 해보았습니다. 아직 처음이라 너무 어려웠지만, 어떤 흐름으로 협업이 이뤄지는지 워크플로우를 볼 수 있었습니다. 또한 html, css 그리고 js가 아직 미숙하지만 전체적인 것을 배웠기에 꾸준히 공부를 이어나가 실력을 늘리도록 하겠습니다. 무엇보다 협업을 하기위해서는 깃을 잘해야겠다는 생각을 가집니다.

> **안성민:** 
css에 대한 이해가 부족하여 사진을 화면 크기에 맞게 채우는데 시간이 오래걸렸습니다. git 사용법이 미숙하여 merge하는 과정에서 어려움을 겪었고, 협업에서 git의 중요성을 느끼게 되었습니다. 또한 프로젝트의 버그를 수정하는 과정에서 원인을 찾고 해결방안을 도출해 내는 과정에서 실력이 향상된 것 같습니다.

> **박선주:** 
가상 클래스의 개념이 생소했지만 자료를 보며 차근차근 이해하니 완성 할 수 있었습니다. 변수명을 짓는데 '호버, 포인터, 커서'등 혼란이 있어 변수명을 미리 생각해두는것이 중요하고 추가로 git사용을 연습해야겠다고 느꼈습니다.

> **박은혜:** 
주제를 정할 때만 해도 너무 금방 끝날 수도 있겠다 생각했는데 예상치 못한 이슈가 많았습니다. 하지만 팀원들과 같이 찾아가며 잘 마무리 할 수 있었습니다. 협업을 위해 코드 컨벤션, 원활한 의사소통, GIT 의 중요성을 체감했습니다.
