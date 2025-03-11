# u.u market

### - 구매와 판매가 가능한 오픈 마켓 웹 서비스

- 🥲 서버가 중단되어 서비스가 실행되지 않습니다.
- 👨‍🌾 서버를 새로 구축 중입니다.
- 🙌 이 서비스는 토이 프로젝트로 실제 구매, 판매는 이뤄지지 않습니다.

```
- Next.js 14.0.4 (App router)
- Typescript
- React
 - react-table
 - react-hook-form
- next-auth

State
- zustand

lint
- eslint
- prettier

styling
- scss
- classnames
- figma

Promise based HTTP client for the browser
- axios
```

## **구현 페이지**

1)로그인 페이지 2) 회원가입 페이지 3) 상품목록 페이지 4)상품 상세 페이지 5) 장바구니 페이지 6) 주문/결제 페이지 7)판매자 센터 페이지 8) 상품 등록 페이지

## 페이지 별 디테일 및 기능 설명

### [로그인 페이지]

    - 구매회원, 판매회원 구분
    - 유효성 검사
        - Input UI: 입력 전, 입력 중, 오류 시 input border color 변경
        - 경고 문구, Input focus : 아이디나 비밀번호가 일치하지 않거나, 아이디나 비밀번호를 입력하지 않았을 때, 입력 창에 입력이 안된 부분이 존재한 채로 로그인 버튼을 눌렀을 때
        - 입력 창 아래에 경고창이 나타나면 로그인 버튼을 눌러도 로그인 되지 않음
        - 로그인 완료시 메인 페이지로 이동

### [회원가입 페이지]

    - 모든 입력을 완료하고 동의하기 체크를 해야만 회원가입이 가능
    - 중복 검사:
      - 개별 버튼 : 아이디, 사업자 등록번호(판매자)
      - 회원가입 버튼 : 휴대폰 번호, 스토어명
    - 토스트 메세지: 동의하기 체크박스, 중복검사 버튼 확인 안할 시
    - 비밀번호 일치 여부 확인 - input 입력시 자동 체킹
    - 회원가입 완료 시 토스트 메세지가 띄워지고 메인 페이지로 이동
    - 유효성 검사
        - 아이디 : 20자 이내의 영어 소문자, 대문자, 숫자만 가능
        - 비밀번호 : 8자~18자, 영소문자, 1개 이상의 숫자, 특수문자 포함
        - 휴대폰 번호: 01* 로 시작하는 10~11자리 숫자, 가입된 번호 확인

### [상품 목록 페이지]

    - 목록에서 상품을 클릭하면 상품 상세 페이지로 이동
    - 판매자 센터에서 상품이 등록되면 상품 목록 페이지에도 동일한 상품이 나타남
    - 로딩 중일 때 스켈레톤 UI
    - 목록 무한스크롤

### [상품 상세 페이지]

    - 수량 변경 가능
    - 수량을 변경할 때 현재 상품의 재고 수량을 초과하면 alert
    - 선택된 옵션에 맞춰서 가격을 계산하고, 총 가격이 나타남
    - 로딩 중일 때 스켈레톤 UI
    - 구매자 일 때
        - ORDER 버튼 클릭 시, 결제 페이지로 이동
        - CART 버튼 클릭 시, 장바구니 페이지로 이동, 상품이 담김
    - 판매자 회원 일 때 ORDER ,CART 버튼 비활성화
    - 비로그인 회원일 때 CART , ORDER 버튼 클릭 시 모달창으로 로그인 안내

### [장바구니 페이지]

    - 장바구니에서 상품의 수량을 수정할 때, +나 - 버튼을 누르면 수량 수정을 위한 모달창이 나타남
    - 상품금액과 할인, 배송비가 적용되어 총 결제할 가격이 계산됨
    - 이미 장바구니에 넣은 제품을 다시 넣는 경우, 이전 수량과 합쳐짐
    - 상품 개별 삭제 : 상품의 X 버튼을 클릭할 시 상품 삭제됨
    - 전체 삭제 버튼: 클릭시 상품 전체 삭제됨 (장바구니에 상품이 없을 때는 비활성화)

### [페이지 상단 글로벌 네비게이션 영역(GNB)]

    - 구매 회원 : 장바구니 버튼, 로그아웃 버튼
    - 판매 회원:  판매자 센터 버튼, 로그아웃 버튼
    - 비로그인 회원 : 장바구니 버튼, 로그인 버튼
        - 장바구니 버튼을 클릭시 로그인 페이지로 이동

### [주문/결제 페이지]

    - 배송 정보 칸에 주문자 정보와 배송지 정보를 입력
    - 모든 입력이 완료되어야 결제하기 버튼이 활성화
    - 결제하기 버튼을 누르면 결제가 진행
    - 결제가 완료되면 주문 완료 페이지로 이동

### [판매자 센터 페이지]

    - 상품 업로드 페이지에서 등록한 상품들이 판매 상품 목록에 보여짐
    - 수정 버튼을 누르면 상품 업로드 페이지로 이동, 상품 업로드 페이지에는 등록한 상품에 해당하는 상품의 내용이 보여짐

### [상품 업로드 페이지]

    - 상품 이미지 등록(상세페이지와 상품목록페이지에서 보이는 이미지)
    - 상품명, 판매가, 기본 배송비, 재고, 상품 설명 입력
    - 저장하기 버튼 클릭 시 상품 등록, 등록 완료되면 토스트 메세지, 상품 상세 페이지로 이동

## 개발 기록

1. next12 + 리액트 쿼리
   -> next app router로 마이그레이션

2. 무한스크롤 제거, 더보기 버튼 추가
   -> vercel 배포 환경에서 무한스크롤 로딩이 너무 느린 문제 발생
   -> 유저 대기 시간 줄이기 위해 더보기 버튼으로 대체

3. 상품목록, 디테일 페이지 스캘래톤 UI 적용

## 트러블 슈팅

1. `폴더트리`

   - 상품 목록 params

2. `회원가입 시 Axios Instance가 동작을 안함.`

   [문제파악]
   회원가입 form 내 요청함수들이 CSR로만 동작함.

   원인을 찾아보니 회원가입 폼에서 사용하고 있는 `React Hook Form` 이 CSR 에서 폼을 관리하기 위한 라이브여서 주로 CSR 환경에서 사용이 된다고 함

   [해결방법]
   CSR 에서 사용할 axios instance를 생성해서 client side 에서 동작하도록 함.

   ```tsx
   //(기존) 이렇게 작성했을때 함수가 동작하지 않음.
   checkIdValid: (username: string) => {
   return axiosAuth.post(`signup/valid/username/`, { username });
   };

   //(수정후) client side의 axios instance가 동작.
   checkIdValid: (username: string) => {
   return axiosClient.post(`accounts/signup/valid/username/`, { username });
   },
   ```

3. `next auth session 에 token 저장`

   session에 res 데이터를 넣고 싶은데 user 이 빈 객체가 되는 문제 발생. 리서치 후 아래와 같이 작성하니 동작

   ```ts
   callbacks: {
    jwt: async ({ token, user }) => {
      user && (token.user = user);
      return token;
    },
    session: async ({ session, token }) => {
      /*@ts-ignore */
      session = token.user;
      return session;
    },
   },
   ```

4. `Error: An error occurred in the Server Components render`

   [문제파악]
   오랜시간 접속하지 않았을 경우 해당 에러 발생.
   쿠키의 next-auth 관련 변수들 제거하니 오류 안남.
   즉 로그아웃이 되면 해당 에러가 발생하지 않음.
   만료된 토큰을 RootLayout에서 가져오고 있어서 페이지 접근이 안된것으로 보임. 만료된 토큰임을 확인하는 로직이 필요

   [해결방법]
   **페이지 진입시 유저 토큰이 유효한지 판단 후 로그아웃 시키기.**
   유효한 토큰인지 확인이 필요함.
   백엔드에서 refresh token, verify token api 를 제공하지 않음. axios 에러가 났을 때 axiosInterceptor에서 로그아웃 처리함으로써 해결

```ts
//axios interceptor 에서 response.status === 401 일때 세션 제거를 통해 로그아웃 처리

axiosAuth.interceptors.response.use(
  (response) => {
    return response;
  },
  async (error) => {
    const { response } = error;

    if (response.status === 401) {
      originRes.cookies.delete('next-auth.session-token');
      return originRes;
    } else {
      // 기타 에러 처리
      return Promise.reject(error);
    }
  },
);

//토큰은 있는데 user_type 이 쿠키에 저장되어 있지 않은 경우
if (token && !user) {
  originRes.cookies.delete('next-auth.session-token');
  return originRes;
}
```
