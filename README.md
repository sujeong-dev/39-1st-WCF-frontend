## 👕 위코드가 사랑하는 패션, WCF

<br />
<img width:"100%" src="https://user-images.githubusercontent.com/98579539/204131960-1f61d815-1da8-407e-b5f8-76ad620f81e2.gif" />

<br />

## 👏 소개

SSF SHOP을 모티브로한 의류 소개 사이트

<br />

## 💡 서비스

👤 회원가입 및 로그인 <br />
👕 위코드 멘토님들 및 동기분들의 의류소개<br />
✏️ 카테고리 별 브랜드 검색 및 필터링<br />
🛒 장바구니

<br />

## 🚀 실행방법
```zsh
$ git clone https://github.com/sujeong-dev/39-1st-WCF-frontend.git
$ git pull origin main
$ npm install
$ npm start
```
<br />

## 🔧 사용하는 기술스택

![](https://velog.velcdn.com/images/sujeong_dev/post/d46cd72c-b2e6-421b-822d-5dd1bb88b45c/image.png)

<br />

## ⭐️ 프로젝트 구조
```
.
├── Router.js
├── components
│   ├── Footer
│   │   ├── Footer.js
│   │   └── Footer.scss
│   └── Nav
│       ├── MainCtgData.js
│       ├── Nav.js
│       ├── Nav.scss
│       └── SpecialCtgData.js
├── config.js
├── images
│   ├── cart
│   │   ├── IMG_8905.JPG
│   │   ├── bag.png
│   │   ├── basket-img.png
│   │   ├── bg-component.png
│   │   ├── btn-x.svg
│   │   └── btn_x_gray.svg
│   ├── icon
│   │   ├── btn-sprite.png
│   │   ├── heart-stripe.png
│   │   ├── plus-minus-stripe.png
│   │   ├── signin
│   │   │   ├── term-check-off.svg
│   │   │   ├── term-check-on.svg
│   │   │   ├── term-check.svg
│   │   │   ├── vaild-check-purple.svg
│   │   │   └── valid-check.svg
│   │   ├── sns-icons.png
│   │   └── star-spripe.png
│   └── productdetail
│       └── banner-1.jpg
├── index.js
├── pages
│   ├── Cart
│   │   ├── Cart.js
│   │   ├── Cart.scss
│   │   └── components
│   │       ├── CartEmpty.js
│   │       └── CartFilled.js
│   ├── Login
│   │   ├── Login.js
│   │   └── Login.scss
│   ├── Main
│   │   ├── HotBrand.js
│   │   ├── HotBrand.scss
│   │   ├── Main.js
│   │   ├── Main.scss
│   │   ├── Marketing.js
│   │   ├── Marketing.scss
│   │   ├── OUR_PICKS.js
│   │   ├── OurPicks.js
│   │   └── OurPicks.scss
│   ├── MyPage
│   │   ├── MyPage.js
│   │   └── MyPage.scss
│   ├── Payment
│   │   ├── Payment.js
│   │   └── Payment.scss
│   ├── ProductDetail
│   │   ├── CartConfirm
│   │   │   ├── CartConfirm.js
│   │   │   └── CartConfirm.scss
│   │   ├── ImgArea
│   │   │   └── ImgArea.js
│   │   ├── ProductDetail.js
│   │   └── ProductDetail.scss
│   ├── ProductList
│   │   ├── Brand
│   │   │   ├── Brand.js
│   │   │   └── Brand.scss
│   │   ├── Price
│   │   │   ├── Price.js
│   │   │   └── Price.scss
│   │   ├── Product
│   │   │   ├── Product.js
│   │   │   └── Product.scss
│   │   ├── ProductList.js
│   │   ├── ProductList.scss
│   │   └── Size
│   │       ├── Size.js
│   │       └── Size.scss
│   └── SignIn
│       ├── SignIn.js
│       ├── SignIn.scss
│       └── termData.js
└── styles
    ├── common.scss
    ├── reset.scss
    └── variables.scss
```

<br />

## ✏️ 인상깊은 코드
### 2-1. 탭 별 조건부 렌더링

![](https://velog.velcdn.com/images/sujeong_dev/post/30261ee7-6244-4b83-8ccb-2ab67f538670/image.gif)

리스트페이지에서 조건부 렌더링을 통해 탭 레이아웃 구현

**👇 ProductList.js**
```jsx
const TABS = [
    {
      id: 0,
      title: '브랜드',
      content: <Brand />,
    },
    {
      id: 1,
      title: '가격',
      content: <Price />,
    },
    {
      id: 2,
      title: '사이즈',
      content: <Size />,
    },
  ];

            <div className="left-filter">
              <ul className="filter-list">
                {TABS.map(filter => {
                  const isCurrent = currentTab === filter.id;
                  return (
                    <li key={filter.id}>
                      <button
                        onClick={() =>
                          setCurrentTab(isCurrent ? '' : filter.id)
                        }
                        className={isCurrent ? 'current' : ''}
                      >
                        {filter.title}
                      </button>
                    </li>
                  );
                })}
              </ul>
            </div>
          {TABS.find(({ id }) => id === currentTab)?.content}

```
> - `TAB`객체를 활용하여 id, content를 매칭하여 조건부 렌더링 구현
- `map`을 돌려 `title`을 불러와 필터링 버튼을 생성하고 click시 현재 tab의 id값을 설정한다.
- 현재 tab의 id를 `TAB`객체에서 찾아 해당하는 id의 content인 컴포넌트를 불러온다.
- `옵셔널체이닝`을 통해 `TAB`객체에서 현재 tab의 id가 없는 경우, 즉 tab이 다 닫혀있는 경우 content를 불러올 수 없기 때문에 예외처리를 해주었다.
** 현재 열려있는 tab을 한번 더 click시 현재 tab의 id와 `TAB`객체의 id가 같은 지 판별하여 현재 tab의 id를 reset하여 toggle기능 구현

### 2-2. querystring
브랜드, 가격, 사이즈의 정보를 querystring으로 담아 필터링 구현

**👇 Brand.js**
```jsx
const [searchParams, setSearchParams] = useSearchParams();

  //TODO: 브랜드 검색기능
  const searchBrand = e => {
    const filterBrand = BRAND.filter(brand =>
      brand.name.includes(e.target.value)
    );
    setFilterList(filterBrand);
  };

  //TODO: querystring 생성
  const prevQuery = searchParams.getAll('brandId');
  const handleCheckbox = e => {
    const { checked, value } = e.target;
    if (checked) {
      searchParams.append('brandId', value);
      setSearchParams(searchParams);
    } else {
      searchParams.delete('brandId');
      prevQuery
        .filter(query => query !== value)
        .forEach(query => searchParams.append('brandId', query));
      setSearchParams(searchParams);
    }
  };
```
> - checkbox에 check가 되었으면 searchparams에 append()를 통해 추가한다.
- check가 해제되었으면 해당 param key의 value들을 모두 삭제하고 이전에 모든 value들을 담아놓은 `prevQuery`변수에서 e.target.value인 것들을 제외한 value들을 다시 searchparams에 담는다.


### 2-3. path parameter를 통한 동적라우팅
![](https://velog.velcdn.com/images/sujeong_dev/post/666a5342-2b4b-4058-a104-f79b03164847/image.gif)

**👇 Product.js**
```jsx
    <li>
      <Link to={`/product-detail/${id}`}>
        <img src={imgurl} alt="상품이미지" />
        <div className="like" />
        <div className="info">
          <span className="brand">{brand}</span>
          <span className="name">{name}</span>
          <span className="price">{Number(price).toLocaleString()}</span>
          <span className="heart">
            <i className="fa-regular fa-heart" />
            <em>999+</em>
          </span>
        </div>
      </Link>
    </li>
```
**👇 Router.js**
```jsx
    <BrowserRouter>
      <Nav />
      <Routes>
        <Route path="/" element={<Main />} />
        <Route path="/product-detail/:productId" element={<ProductDetail />} />
        <Route path="/product-list" element={<ProductList />} />
      </Routes>
      <Footer />
    </BrowserRouter>
```
> - `Router.js`의 path prop에 `:productId`로 이름을 지정한다.
- 상품리스트페이지에서 어떠한 품목을 선택해도 상품 상세페이지로 이동하게된다.

<br />

## 💡 협업 방법

- Notion과 Trello를 사용하여 scrum, sprint 진행
- GitBook과 Postman을 활용하여 API 및 mockdata형식 공유 <br />

### 협업 tools 및 개발규칙는 [위키](https://github.com/wecode-bootcamp-korea/39-1st-WCF-frontend/wiki) 참조

<br />

## ❤️ 팀원

`FrontEnd`

<table>
  <tbody>
    <tr>
      <td align="center"><a href="https://github.com/sujeong-dev"><img src="https://avatars.githubusercontent.com/u/112826154?v=4" width="100px;" alt=""/><br /><sub><b>구수정</b></sub></a><br /></td>
      <td align="center"><a href="https://github.com/myp880"><img src="https://avatars.githubusercontent.com/u/48706649?v=4" width="100px;" alt=""/><br /><sub><b>박문영</b></sub></a><br /></td>
      <td align="center"><a href="https://github.com/OHJUHYUNG"><img src="https://avatars.githubusercontent.com/u/98579539?v=4" width="100px;" alt=""/><br /><sub><b>오주형</b></sub></a><br /></td>
      <td align="center"><a href="https://github.com/Hyommm"><img src="https://avatars.githubusercontent.com/u/109214539?v=4" width="100px;" alt=""/><br /><sub><b>정효원</b></sub></a><br /></td>
     <tr/>
  </tbody>
</table>
- 구수정 : 상품 리스트 페이지 <br />
- 박문영 : 상품 상세 페이지 <br />
- 오주형 : 로그인 및 회원가입 페이지, 장바구니 페이지 <br />
- 정효원 : 메인페이지(navbar, footer) <br />
<br />

`BackEnd`

<table>
  <tbody>
    <tr>
      <td align="center"><a href="https://github.com/Seoya0512"><img src="https://avatars.githubusercontent.com/u/87962966?v=4" width="100px;" alt=""/><br /><sub><b>이영서</b></sub></a><br /></td>
      <td align="center"><a href="https://github.com/pso0301"><img src="https://avatars.githubusercontent.com/u/112918378?v=4" width="100px;" alt=""/><br /><sub><b>박상욱</b></sub></a><br /></td>
     <tr/>
  </tbody>
</table>
- 이영서 : DB 모델링, 로그인 회원가입/상품 리스트 조회/상품 조회 API <br />
- 박상욱 : DB 모델링, 장바구니 API
