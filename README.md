## Demo Link
[https://vue-blog-3e728.web.app/home](https://vue-blog-3e728.web.app/home)



## 제작 기간

6월 21일 ~ 6월 24일    
1인 개발




## 프로젝트 개요

개발을 하면서 필요한 지식들과 개발 과정의 트러블 슈팅 과정을 기록하고 필요시 열람하기 위한 블로그입니다. CRUD 일부 create / read를 구현하였으며, firebase DB와의 비동기 통신과 기본적인 블로그 기능들을 구현하였습니다. 

Vue 3 / Vuex / Scss 를 사용하였습니다. 페이지 디자인은 kakao brunch 디자인을 참고했습니다.  
- 반응형
- DB(Firebase)를 이용한 CRUD 일부(create-read) 구현
- 새 데이터 입력시 실시간 반영(글, 카테고리)
- 라우팅 구현
  

## 주요 기능 

### 기기에 따른 반응형 디자인구현 

- 800px 이하 모바일, 태블릿 / 800px 이상 웹


### 라우터 구현

- 랜딩 페이지 / 게시글 열람 / 게시글 작성 / 게시글 리스트 페이지로 구분

- 각 게시물의 키 값으로 열람페이지에서는 title 값을, 게시글 리스트 페이지에서는 category 값을 받아 중첩 라우팅 구현


### DB 게시판 구현

- 홈 버튼 구현, 모바일 접속시 상단 중간 홈 버튼 고정 및 blur 스타일링  
![blog08](https://user-images.githubusercontent.com/68191058/179524527-d1614276-630d-412f-8299-c59aeb64c9a7.gif)  

- 글 작성, Github 페이지 이동 버튼 구현

- Vuex 내 액션 함수 비동기 호출을 통한 firebase DB 접근과 데이터 수신시 mutation을 통한 state 갱신

- firebase DB로부터 받아온 post 데이터( title / subTitle / contents / date / category ) 에 대해 Card 형태의 컴포넌트로 props 전달 및 정보 출력  
![blog03](https://user-images.githubusercontent.com/68191058/179523990-2ed228ad-1292-433e-8204-42dbd4189026.gif)  

- firebase DB로부터 받아온 데이터 내 개별 데이터에서 Key 들은 구조분해할당을 통해 구분 후 각각 다른 스타일 속성 부여하여 구분 가능

- Card 컴포넌트 상단 마우스 커서 유무에 따른 hover effect 구현  
![blog01](https://user-images.githubusercontent.com/68191058/179523671-7486f4ff-48ec-4e7c-b638-a788e0f32233.gif)  

- Card 컴포넌트 클릭시 라우터링크를 통한 /view-post:title 페이지로 이동  
![blog04](https://user-images.githubusercontent.com/68191058/179524151-a370380c-9042-45b1-b10d-c0b505d9e2e6.gif)  


### 게시글 열람 페이지 구현

- position: fixed 를 통해 title, subTitle, date 등의 정보가 담긴 레이아웃과 content, category가 담긴 레이아웃 구분(스크롤시 title/subTitle,date 정보 감춰짐)

- content 하단 category 클릭시 해당 category로 작성된 모든 작성글 리스트가 출력된 /post-list/:category 페이지로 이동. post-list/:category 의 경우 클릭된 카테고리의 params를 받아 리듀서 내 post 데이터 내 category 배열 안에 params(클릭 된 category 정보) 와 같은 category명칭을 가진 index가 있는지 확인 후 배열 형태로 저장  
![blog06](https://user-images.githubusercontent.com/68191058/179524337-e6524756-3410-4c8c-b1f2-f5b0dc825b3f.gif)![blog07](https://user-images.githubusercontent.com/68191058/179524430-1cd3484c-52fb-401f-9ec1-789693a5a70d.gif)  


- 열람 페이지 하단 '다른 포스트' 열람 기능 구현. 게시글 열람시 해당 게시글 index 정보를 받아오고 해당 게시글 포함, 게시글의 index 위아래 2개, 총 5개의 post 정보를 배열 형태로 받아 title/date 정보 출력. 최상단, 최하단 게시글의 경우 예외처리를 통해 배열 내 index 부재로 인한 오류 방지  
![blog05](https://user-images.githubusercontent.com/68191058/179524245-8553bcfa-d4f1-421d-9e44-b98c6379e665.gif)  


### 게시글 작성 페이지 구현

- 카테고리 입력후 Enter keydown 시 해당 input props를 받아 하단에 카테고리 항목 블록 생성 구현  
![blog09](https://user-images.githubusercontent.com/68191058/179524610-f53935cd-00e7-47a6-a65c-90fb4e9cd999.gif)![blog10](https://user-images.githubusercontent.com/68191058/179524768-49425bcd-deb8-4b97-a61f-4a0743bace4e.gif)  

- 작성하기 버튼 클릭시 입력받은 title/subTitle/category배열/date/글번호/content/content 요약 정보가 객체에 담기고 vuex 액션함수 호출 및 firebase DB로 객체 업데이트 및 Home 페이지로 이동 구현  
![blog11](https://user-images.githubusercontent.com/68191058/179524894-c22a5805-0361-4e8c-953a-cd7b3a2612c9.gif)  

- text-editor 라이브러리 Quill을 사용한 내용 입력 





## 기술 스택

- vue 3, vuex, firebase
- node-sass, sass-loader, vue-router, quill




## 회고

#### CRUD 프로젝트 진행 간 Vue2, Vue3의 문법적 차이와 장단점, 리액트와의 프레임워크 특성 비교를 중심으로

CRUD는 자바스크립트 웹 페이지 구현에 있어 필수적인 항목입니다. 특정 라이브러리 기능을 실제로 사용할 때 CRUD로 구현하기 가장 간단한 블로그 페이지를 우선적으로 구현해보는 습관이 있습니다. Javascript, React, Redux/redux-thunk, Vue 2, Vue 3, Vuex를 각각 다뤄보고 배울 때 CRUD 방식의 블로그를 제작했습니다.

기존에 Vue 2 / Vuex로 구현했던 블로그 대신 Vue3를 사용해 구현한 프로젝트입니다. Vue3는 기존 베타 버전에서 22년 초 정식 버전으로 릴리즈 되었으나, Meta 주도하 유지보수가 이뤄지는 리액트에 비해 그 생태계가 상당히 작고 아직은 미래가 불투명하다는 단점이 있습니다. 이전 버전인 Vue2 생태계에 비해서도 호환 가능한 라이브러리가 아직 부족한 점, 업계에서 사용되던 Vue2 레거시 코드에서 Vue 3로의 마이그레이션이 이뤄지지 않은 기업이 있다는 점, 최근 Vue 창시자인 에반 유의 정치적 발언 물의 등 내외적인 요인들이 Vue를 계속 학습해나가는 데 있어 장애 요소로 작용합니다.

CSS in JS가 디폴트로 되어있는 SFC(Single File Component) 문법으로 파일을 넘나드는 번거로움이 줄었다는 점과 초반 러닝커브가 낮은 부분, 별도의 간단한 디렉티브의 존재와 렌더링 퍼포먼스에 있어 리액트보다 빠른 점, react-redux와 비교하여 Vuex 사용이 간편하다는 점이 프레임워크로서 리액트와는 차별화되는 Vue의 강점입니다.

이번 프로젝트를 진행하며, Vue 2와 비교하여 Vue3에서 강력하다 생각한 문법은 setup 함수입니다. 기존 data / computed / methods / watch 컴포넌트 모듈들을 선언하는 방식과 달리 이를 setup 함수 내에서 모두 처리할 수 있었으며, this 바인딩에 대한 신경을 덜 써도 되고, 가독성이 향상되는 경험을 했습니다. 또한 외부 컴포넌트로부터 받아오는 props와 라이프사이클 훅 또한 setup 함수 내에서 처리 할 수 있었습니다. 해당 문법을 통해 Vue2 에 비해 Vue3는 리액트 사용 방식과 유사해졌다는 인상을 받았습니다. 하지만 보안상의 이유인지 setup 함수로 props나 데이터를 들여오는 과정에서 기존 모듈 형식과 달리 데이터가 1차 래핑된 형식으로 들어와서 해당 데이터의 로그를 출력해 뜯어보고 난 후에야 이해할 수 있었다는 점과 Vue3에서 기존 Vue2 방식의 모듈 선언은 가능하나 해당 모듈들의 데이터와 메서드는 setup 함수와 호환이 되지 않는다는 점은 처음 Vue3를 사용하며 아쉽다고 생각한 점입니다.

정리하면, 기존 Vue의 강점이었던 CSS in JS의 경우 리액트에서도 대체 라이브러리들이 많아 큰 강점이라 생각하기 힘듭니다. Vue2에서의 가독성과 협업, 유지보수에 유리한 일관성 있는 코드 작성이 가능하다는 장점이 Vue3로 와서 코드가 줄어드는 방식으로 더 극대화 되긴 했으나, 이 방향성이 프레임워크 생태계 내에서 리액트와의 경쟁에 있어 큰 우위를 가져가는지는 더 지켜볼 필요가 있습니다. 무엇보다 기존 Vue2에서 호환이 되던 라이브러리들이 업데이트 지연을 이유로 Vue3에선 호환이 되지 않아 적용 가능한 버전을 찾는 데 시간을 추가로 들여야 된다는 점, 필수 문법인 setup 함수가 기존 Vue2 모듈 문법과 호환이 되지 않는다는 점이 기업들의 대규모 레거시 마이그레이션에 장애 요소가 될 수 있겠다는 생각이 들었습니다.
