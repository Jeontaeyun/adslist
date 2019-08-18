# [토이 프로젝트] 뷰와 LESS를 이용한 광고 리스트

## 01. 프로젝트 개요

### (01) 프로젝트 아키텍쳐

- 프레임워크 : Vue.js
- CSS 전처리기 : LESS
- CSS 프레임워크 : 부트스트랩
- HTTP 통신 : Axios

### (02) 프로젝트 목적 

선언형 점진적 웹 뷰 프레임워크 Vue.js와 LESS를 이용하여 게시글 리스트를 불러오는 프로젝트. 해당 프로젝트를 통해서 Vue.js와 LESS에 대해 알아보고 프로젝트 환경 설정 및 간단한 화면을 구성해보기 위한 프로젝트입니다. 해당 프로젝트를 통해 다음과 같은 목적을 달성할 것 입니다.

- Vue.js 프레임워크의 사용법 학습

- LESS와 Vue.js의 연결과 프로젝트 환경 설정법 학습

- LESS의 사용법 학습

## 02. 프로젝트 이론

### (01) Vue.js 프로젝트 생성 및 LESS 연동 방법

#### Vue 프로젝트 생성

vue-cli를 이용하면 쉽게 vue 프로젝트와 웹팩 환경을 설정할 수 있다. vue-cli를 설치 후 init 명령어를 통해 프로젝트를 생성할 수 있다.

```bash
$npm i vue vue-cli

$vue init webpack-simple
```

구분                        | 설명
---------------------------| --------------------------------------------------------------------
vue init webpack           | 고급 웹팩 기능을 활용한 프로젝트 구성방식. 테스팅, 문법 검사 등을 지원
vue init webpack-simple    | 웹팩 최소 기능을 활용한 프로젝트 구성 방식. 빠른 화면 프로토타이핑 용
vue init browserify        | 고급 브라우저파이 기능을 활용한 프로젝트 구성 방식. 테스팅, 문법 검사 등을 지원
vue init browserify-simple | 브라우저파이 최소 기능을 활용한 프로젝트 구성 방식. 빠른 화면 프로토타이핑 용
vue init simple            | 최소 뷰 기능만 들어간 HTML 파일 1개 생성 
vue init pwa               | 웹팩 기반의 프로그레시브 웹 앱(PWA) 기능을 지원하는 뷰 프로젝트

또한, 웹팩에서 뷰의 싱글 파일 컴포넌트 체계를 사용하기 위해서는 .vue 파일을 읽어줄 수 있는 뷰 로더 기능을 추가해야 한다. 웹팩은 자바스크립트 모듈만 인식할 수 있기 때문에 뷰 로더가 .vue 파일을 일단 자바스클립트 모듈로 변환합니다.

또한 필요에 따라 웹팩의 추가 플러그인을 이용하면 웹팩으로 변환된 자바스크립트 모듈을 CSS나 HTML 파일로 분리할 수 있습니다.

> **싱글 파일 컴포넌트 체계**
>
> 애플리케이션의 규모가 커서 기능별로 관리를 해야 할 경우에는 <components/기능/컴포넌트.vue>와 같은 형식으로 관리하는 것이 좋습니다.

#### 웹팩과 LESS 연동

Vue 프로젝트에 LESS를 연동해주기 위해서 less 와 less-loader를 설치한 후 웹팩 설정에 넣어서 웹팩 환경의 Vue 프로젝트에서 LESS를 사용할 수 있도록 해줍니다.

[ less와 less-loader 설치 ]

```bash
$npm i less less-loader
```

[ webpack.config.js 설정 ]

```javascript

module.exports = {
    module: {
		rules: [
            ...
            {
                test: /\.less$/,
				use: [ 'vue-style-loader', 'css-loader', 'less-loader' ]
            }
        ]
    }
}

```

#### 뷰 기본 개념

용어              | 설명 
---------------- | -----------------------------------------------------------------------------
뷰 View | 사용자에게 보이는 화면. UI를 말한다
돔 DOM | HTML 문서에 들어가는 요소(태그, 클래스, 속성 등)의 정보를 담고있는 데이터
돔 리스너 | 돔의 변경 내역에 대해 즉각적으로 반응하여 특정 로직을 수행하는 장치
모델 | 데이터를 담는 용기. 보통은 서버에서 가져온 데이터를 자바스크립트 객체 형태로 저장
데이터 바인딩 | 뷰(View)에 표시되는 내용과 모델의 데이터를 동기화
뷰 모델 | 뷰와 모델의 중간 영역. 돔 리스너와 데이터 바인딩을 제공하는 영역

## 03. 프로젝트 고찰

### (01) 익숙하지 않은 프레임 워크를 사용하는 연습

  프로그래머로 성장하기 위해서 첫 번째 해야할 일이 하나의 분야(언어든, 프레임워크든, 분야든)를 일정 수준 정복하는 것이라고 생각했다. 그 다음 과정은 내게 익숙하지 않은 프레임 워크를 사용하는 것을 당연하게 받아들일 용기이다.

  해당 프로젝트를 짧은 기간 동안 진행하며 Vue.js는 쉽다는 주변 평판과 다르게 어느정도 어려웠다. 과거에 Vue.js를 잠깐 해본 적이 있어 이벤트 처리와 props 정도는 알았지만, 어떻게 Axios와 연동하고 Less와 연동하는지 등은 정말 어려웠다.

  특히, React 폴더 구조에 익숙한 탓인지 기본적인 Vue가 아닌 싱글 파일 컴포넌트 체계를 사용하여 프로젝트를 진행하는 것은 공식 문서를 보고 이해하며 적용하는데 한 차례 더 어렵게 느끼게 했다.

  하지만, 다양한 참조 문헌을 참고하여 인피니트 스크롤링과 Axios 처리 등을 다 한 후, 해당 코드를 다시 리팩토링하며 정리해보고자 한다. 해당 프로젝트의 고찰은 Vue에 대항 내용을 정리한다.  

  01. 라우팅 방식, CSS 방식 등 기존의 리액트와 대부분 비슷한 컴포넌트 방식이기에 이 부분은 러닝 커브가 낮앗다.

  02. 하지만, 인피니트 스크롤링, Axios처리와 같이 데이터 바인딩에 러닝 커브가 높았다.

  03. 이번 프로젝트에서 Vue의 **데이터 바인딩 방식**과 **라이프 사이클**만 익히는 것이 중요하다.

### (02) 인피니트 스크롤과 정렬 기준을 바꾸기 위한 watch

 Vue.js를 다루면서 Axios를 이용해 데이터를 불러오는 것에 고민이 많았다. data()에 page와 ord 를 넣어도 이벤트가 발생해도 템플렛에 해당 값이 없기에 리렌더링이 일어나지 않았다. 여러 자료를 검색한 후 Axios와 같이 비동기 데이터 API 호출에는 watch가 유용하다는 것을 알았다.

 watch는 해당 data()값이 변하면 특정 동작을 수행해주는 속성이며 다음과 같이 기술할 수 있다.

```javascript

 watch: {
     dataValue : function () {
         ...
     }
 }

 ```

 ### (03) 크로스 브라우징

 해당 프로젝트에서 크로스 브라우징을 시도하였다. 지원하는 브라우저와 버전은 다음과 같다.

 브라우저 | 크롬 | 엣지 | 파이어폭스 | 사파리 | IE
 버전 | 76.0.3809.100 < | ? | 68.0.2 < | 12.1.1 < | ?