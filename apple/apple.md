# apple 제품 카드

### Apple 마크업

<img src="https://github.com/Jisoo0907/homework/assets/102653945/d3e504f1-a073-4977-9c5f-bb750f1dccc7" width="400" height="400">

- 제품 광고는 일종의 콘텐츠 영역이라 **전체 영역**을 `section`태그로 묶음
- 각 제품 광고는 독립적인 콘텐츠 항목이라 **각 카드 영역**을 `article`태그로 묶음
- 상단의 **제목**은 제품명을 뜻하므로 `h1`태그로 묶음
- **부제목**은 제품에 대한 간략한 설명으로 `h2`태그로 묶음
- **출시일 추후 공개**는 하나의 단락으로 볼 수 있어 `p`태그로 묶음
- 아래의 **버튼**들은 `div`로 하나의 그룹으로 묶고, 각각을 `button`으로 작성함

### CSS

#### 레이아웃

- 중복된 요소를 하나의 컴포넌트로 만들면 편하겠다고 생각함
- 처음 봤을 때 눈에 띄었던 건 버튼 두 개와 각각의 카드 구조였음

  > **버튼**<br/>
  > 채워진 파란색 버튼 <br/>
  > 빈 파란색 버튼 <br/>
  > 채워진 검정색 버튼 <br/>
  > 빈 검정색 버튼<br/>

  > **카드**<br/>
  > 제목, 부제목, 텍스트 단락, 버튼 <br/>
  > 구조가 모두 똑같고 텍스트만 다름<br/>

- 따라서 `button`과 `card` 컴포넌트를 따로 만들었다.
- **button**은 다음과 같이 작성함

  ```html
  <body>
    <div class="button-group">
      <button type="button" class="blue-fill-btn">더 알아보기</button>
      <button type="button" class="blue-btn">가격 보기</button>
    </div>
  </body>
  ```

  ```css
  /* 버튼 공통 스타일 */
  button {
    padding: var(--small-spacing) var(--small-spacing);
    border-radius: 25px;
    border: 0;
    background-color: transparent;
  }

  /* 파란 버튼 스타일링 */
  .blue-fill-btn {
    background-color: var(--blue-200);
    color: var(--white);
    margin-right: var(--base-spacing);

    &:hover {
      background-color: var(--blue-100);
    }
  }
  .blue-btn {
    background-color: transparent;
    border: 1px solid var(--blue-200);
    color: var(--blue-200);

    &:hover {
      background-color: var(--blue-200);
      color: var(--white);
    }
  }
  /* 검정 버튼 스타일링 */
  .black-fill-btn {
    background-color: var(--black);
    color: var(--white);
    margin-right: var(--base-spacing);

    &:hover {
      background-color: #363638;
    }
  }
  .black-btn {
    color: var(--black);
    border: 1px solid var(--black);

    &:hover {
      background-color: var(--black);
      color: var(--white);
    }
  }
  ```

- 결과 화면<br/>
  ![image](https://github.com/Jisoo0907/homework/assets/102653945/f802c94b-49d3-40df-a499-021165402ae3)
  <br/>
- **card**는 다음과 같이 작성함

  ```html
  <body>
    <section class="card-section">
      <article class="card">
        <h1 class="title white">Apple</h1>
        <h2 class="subtitle white">
          놀라우리만치 얇다.<br />엄청나게 강력하다.
        </h2>
        <div class="release">출시일 추후 공개</div>
        <div class="button-group" role="group">
          <button type="button blue" class="blue-fill-btn">더 알아보기</button>
          <button type="button" class="blue-btn">가격 보기</button>
        </div>
      </article>
    </section>
  </body>
  ```

  ```css
  /* small screen */
  .card-section {
    display: grid;
    grid-template-columns: 1fr;
    gap: 20px;
  }
  .card {
    height: var(--size);
    display: flex;
    flex-flow: column nowrap;
    align-items: center;
    background: url(/products/ipad_pro.jpeg) no-repeat center;
    /* 사진의 중앙 부분이 보이도록 함 */
    .title {
      font-size: var(--large-text);
      font-weight: 700;
      margin-bottom: var(--small-spacing);
      padding-top: var(--large-spacing);
    }
    .subtitle {
      font-size: var(--base-text);
      line-height: var(--line-normal);
      margin-bottom: var(--x-small-spacing);
    }
    .release {
      font-size: var(--small-text);
      color: var(--gray);
      margin-bottom: var(--small-spacing);
    }
    button {
      font-size: var(--xx-small-text);
    }
  }
  /* 카드 글자 색상 */
  .white {
    color: var(--white);
  }
  .black {
    color: var(--black);
  }
  /* large screen */
  @media (min-width: 1024px) {
    .card-section {
      grid-template-columns: 1fr 1fr; /* 1024px 넘어갔을 때 열이 두 개가 되도록 */
    }

    .card {
      .title {
        font-size: var(--extra-large-text);
        font-weight: 700;
        margin-bottom: var(--small-spacing);
      }
      .subtitle {
        font-size: var(--medium-text);
        line-height: var(--line-normal);
        margin-bottom: var(--x-small-spacing);
      }
      button {
        font-size: var(--x-small-text);
      }
    }
  }
  ```

- 결과 화면<br/>
  ![image](https://github.com/Jisoo0907/homework/assets/102653945/97b81179-824d-4b2d-93f9-c8fa2b3bfcd3)

- apple.html 파일에 위 카드들을 7개 만들어 각각의 내용에 맞게 수정함
- 코드의 일부

  ```html
  <section class="card-section">
    <article class="card card1">
      <h1 class="title white">iPad Pro</h1>
      <h2 class="subtitle white">놀라우리만치 얇다.<br />엄청나게 강력하다.</h2>
      <p class="release">출시일 추후 공개</p>
      <div class="button-group" role="group">
        <button type="button" class="blue-fill-btn">더 알아보기</button>
        <button type="button" class="blue-btn">가격 보기</button>
      </div>
    </article>

    <article class="card card2">
      <h1 class="title black">iPad air</h1>
      <h2 class="subtitle">
        두 가지 사이즈, 더 빠른 칩.<br />무엇이든 거뜬하게.
      </h2>
      <p class="release">출시일 추후 공개</p>
      <div class="button-group" role="group">
        <button type="button" class="black-fill-btn">더 알아보기</button>
        <button type="button" class="black-btn">가격 보기</button>
      </div>
    </article>
  </section>
  ```

  ```css
  /* small screen */
  .card-section {
    .card1 {
      background: url(/products/ipad_pro_2x.jpeg) no-repeat center;
      background-size: cover; /* 페이지를 늘렸을 때 사진도 같이 커지도록 */
    }
    .card2 {
      background: url(/products/ipad_air_2x.jpeg) no-repeat center;
      background-size: cover;
    }
    .card3 {
      background: url(/products/iphone15_pro_2x.jpeg) no-repeat center;
      background-size: cover;
    }
    .card4 {
      background: url(/products/iphone15_2x.jpeg) no-repeat center;
      background-size: cover;
    }
    .card5 {
      background: url(/products/apple_watch_2x.jpeg) no-repeat center;
      background-size: cover;
    }
    .card6 {
      background: url(/products/macbook_air_2x.jpeg) no-repeat center;
      background-size: cover;
    }
    .card7 {
      background: url(/products/airpods_pro_2x.jpeg) no-repeat center;
      background-size: cover;
    }
  }

  /* large screen */
  @media (min-width: 1024px) {
    .card-section {
      .card1,
      .card2,
      .card3 {
        grid-column: 1 / 3;
      }

      .card3 {
        background: url(/products/iphone15_pro_wide_2x.jpeg) no-repeat;
        background-size: 100% 100%;
      }
    }
  }
  ```

### 최종 결과 화면

- 1024px **이하**일 때 화면
  ![짤1](https://github.com/Jisoo0907/homework/assets/102653945/786c3472-7abc-4403-954e-fa16df424a00)<br/>
- 1024px **이상**일 때 화면(세 번째 사진의 **배경 이미지 변화**)
  ![짤2](https://github.com/Jisoo0907/homework/assets/102653945/6f154865-ced5-4a7c-8499-acccffcef549)<br/>
- 화면 크기를 늘릴 때 **사진도 같이 커지는** 모습
  ![3](https://github.com/Jisoo0907/homework/assets/102653945/8c6ffa0f-4af5-436b-9975-29cf9208b714)<br/>

<br/>

### 후기

- 마지막 과제라는 게 아쉬울 만큼 재밌었다.
- 물론 과제 수행에 엄청 오랜 시간이 걸렸지만...
- 내가 그리드를 제대로 이해하지 못했음을 깨달았다.(사실 지금도 완벽히 이해하진 못했다.)
- 과제를 하면서 조금씩 이해되는 것 같다. (처음에는 display: grid를 어디에 넣어야 하는지 조차 헷갈렸다.)
- 그리고 과제를 시작한 지 8시간 정도 지났을 무렵, 마크업에 문제가 있음을 알아차렸다.
- 초반엔 `div.container>section>article`이런 식으로 작성했다.
- 그랬더니 화면을 늘렸을 때 한 줄에 카드가 두 개가 되지 않고 한 개의 카드 내에서 제목과 텍스트들이 양쪽으로 갈라졌다.
- 마크업을 수정하면 이미 작성한 css파일들도 수정해야 하고...
- 정신이 아득해졌지만 지금 마크업을 수정하지 않으면 어차피 원하는 결과가 나오지 않기에... 최종 작성한 방식으로 수정했다.
- 지금 보니 어차피 카드는 article로 묶여 있는 데 굳이 각각을 또 section으로 한 번 더 묶었나 싶다.
- 마크업 작성은 아직도 너무너무 어려운 것 같다.
