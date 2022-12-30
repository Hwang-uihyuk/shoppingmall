# Shoppingmall Project



## FE


#### firebase set up

    1. Go to Console
    2. Create a Project
    3. Enter your project name (My project name : shoppy-final)
    4. Google Analytics for your Firebase project 
        1. Enable Google Analytics for this project
    5. Authentication
        1. Google Login ⇒ enable로 바꿔주기
    6. Realtime Database
        1. Singapore 이 제일 가까움으로 선택
        2. Start in test mode로 선택
    7. Add Firebase your **web** app
        1. web <> 모양 선택
        2. nickname 아무거나 설정해주고(shoppy-final)

#### Cloudinary set up

    digital media 이미지 그냥 업로드하는게 아니라 더 빠르게 로딩할 수 있고 시각적으로 영향이나 다른 버전들로 만들 수 있게 해준다.

    업로드하면서 우리가 원하는 형태로 줄이거나 키우거나 할 수 있는 장점이 있음.

    1. login ( Google로 로그인했음) 
    2. setting
    3. Upload presets로 매번 올릴때마다 확인안해도됨.

        !(https://s3-us-west-2.amazonaws.com/secure.notion-static.com/13c92a25-16ba-4277-9d06-e2957a8d5803/Untitled.png)

4. env_local에 숨켜서 적용하기
    1. REST API 이용하기!
    2. [https://api.cloudinary.com/v1_1/<cloud](https://api.cloudinary.com/v1_1/<cloud) name>/<resource_type>/upload

```jsx
 REACT_APP_CLOUDINARY_URL=https://api.cloudinary.com/v1_1/drycfsi16/image/upload
 REACT_APP_CLOUDINARY_PRESET=kow0fqaq
```

#### To backend

    현재

    firebase에서 로그인 기능 (google) 구현함

    ⇒ Login연동

    Cloudinary set up에서 데이터를 올릴 수 있는 Rest API를 구현했는데

    만약에 물품을 사용자가 등록을 하면 

    ⇒

#### favicon 바꾸기

    - react icon 홈페이지
        - 검사 - element 원하는 아이콘 선택
        - <svg> … </svg>  element 복사하기
        - svg to ico 검색하기
        - 아무거나 들어가서 변환하기
    - 색상 변경
        - stroke 와 fill을 바꿔주기

#### router(헤더 만들기)

    1.yarn add react-router-dom 

    - 6버전 이상으로 다운로드 하기
    1. index.js
        - createBrowserRouter 로 경로정해주기

            <App>

            / 👉 <Home>

            /products 👉 <AllProducts>

            /products/new 👉 <NewProduct>

            /products/:id 👉 <ProductDetail>

            /carts 👉 <MyCart>



    ```jsx
    -index.js-

    const router = createBrowserRouter([
    {
        path : '/',
        element : <App />,
        errorelement : <NotFound />,
        children : [
    {index : true, path : '/'},
    {path: '/products', element:<AllProducts/>},
        {path: '/products/new', element:<NewProduct/>},
        {path:'/products/:id', element: <ProductDetail/>},
        {path:'/carts',element: <MyCart/>}]
    ]
    )]}

    그 밑 
    render쪽에 
    <RouterProvider router = {router} 해주어야함.
    ```

    - pages 폴더 생성
        - 위에 있는 page들(AllProducts,NewProducts…) 생성하기
    - components 폴더 생성하기
        - Navbar.jsx 생성
            - <Link to =”/”> home </Link>
            - <Link to =”/products”> products </Link> … 링크 생성~
    - App.js
        - <Navbar/> 와 <Outlet/>
        - <Outlet/>
            - Link와 연결된 것들의 모든 것의 element
            
            
            
### tailwind

- in terminal
    - yarn add -D tailwindcss
    - npx tailwindcss init
        - vs code ⇒ tailwind.config.js 생성
    - tailwind.config.js
        - content
            
            ```jsx
            module.exports = {
            	content : ['./src/**/*.{js.jsx}'], 
            	
            
            [] 괄호안에 있는거 추가해주고
            './src/**/*.{js.jsx}'
            ```
            
        - index.css
            - @tailwind base;
            - @tailwind components;
            - @tailwind utilities;
        - index.css styling
            
            

#### firebase login

    - 인증 → web → 하란대로 따라하면 됨.
    - 그곳에 적혀져 있는 대로 하면 안됨. 노출 xx
    - env.local 생성후 key들을 적어줌
    - build - web - google 하란대로 따라하기
    - firebase에서 login 함수 만들어서
    - Navbar쪽에 있는 button에 onClick에 함수를 넣어준다.

#### firebase login & logout 2

    firebase.js와 Navbar.jsx code 정리

#### User profile

    - User에 props로 user를 받아주고
    - User component 생성
    - User component 에 img tag + photoURL을 받아와서 Profile을 등록해준다.

#### 새로고침 login한 상태에서 logout 되는 것 오류 해결

    - Docs → web → get started 맨 마지막
    - firebase.js ⇒ onUserStateChange 함수 생성
    - Navbar ⇒ useEffect로 한 번 만 호출
        - useEffect(function,deps)에서 deps에 빈 배열을 넣어주면, 한 번만 호출


#### ‘Admin’ User vs ‘일반’ User

    - firebase → realtime database에서 data에 admins(권한있는사람)을 만들어주고
    - 그 곳에 해당하는 사람만
    - admins 에 {”0” : “uid”} 설정하기
    - doc → web →읽고 쓰기 확인해서 권한 주기.

    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/caf43dbf-a8d8-4e78-82f3-929535f0b333/Untitled.png)
#### Router-header 

#### pages relation
    <App>
    ./<Home>
    ./products => <AllProducts>
    ./products/new => <NewPRoduct>
    ./products/:id => <ProductDetail>
    ./carts => <Mycart>
  
#### In terminal
      yarn add react-router-dom
      package.json => 'react-router-dom' 확인
  
 #### pages
      AllProducts.jsx
      Home.jsx
      Mycart.jsx
      NewPRoducts.jsx
      NotFound.jsx  ==> url error
      ProductDetail.jsx

 #### Router 
      createBrowserRouter, RouterProvider from react-router-dom
      
      const router = createBrowserRouter([
      {
        path : '/',                                 // home
        element : <App />,                          // home => App component
        errorElement : <NotFound/>,                 // error moment
        children : [                                // children 하위 components
      {index : true, path : '/', element: <Home/>}, // index : true because of path 
      ...
      ])
  
  
 #### Navbar
      <Link to>  =>  url move
  
<p>
<img src="https://img.shields.io/badge/license-mit-green">
<img src="https://img.shields.io/github/issues/hongjin4790/SYE-project">
<img src="https://img.shields.io/badge/tag-v1.0.0-blue">
<img src="https://img.shields.io/badge/Java-007396?style=flat-square&logo=Java&logoColor=white"/>
<img src="https://img.shields.io/badge/Spring-3DDC84?style=flat-square&logo=Spring&logoColor=white"/>
<br>
</p>





# B.E


<!-- TABLE OF CONTENTS -->
<details open="open">
  <summary>Table of Contents</summary>
  <ol>
    <li><a href="#소개">소개</a></li>
    <li><a href="#CRUD">CRUD</a></li>
    <li><a href="#인증과-인가">인증과 인가</a></li>
  </ol>
</details>









## 소개
Shopping mall 프로젝트를 협업하며 구현한내용을 단계별로 작성합니다.

<br><br>

## CRUD
안세준은 적으세요

<br><br>

## 인증과 인가

#### 인증(Authentication)
    사용자의 신원을 검증하는 행위 ex) 로그인

<br>

#### 인가(Authorization)
    사용자에게 특정 리소스나 기능에 액세스할 수 있는 권한을 부여하는 행위 ex) USER, MANAGER, ADMIN..

<br>

#### 사용이유
    Http 프로토콜은 기본적으로 Stateless한 특징을 지니고있어 서버 디자인이 간편합니다.
    하지만 Stateless 하기에 사용자에게 매번 인증에 관한 절차를 묻게됩니다.
    이를 위해 Cookie나 Session을 사용해서 사용자의 불편함을 덜어줍니다.

<br>

#### Spring Security
    Spring Security란 Spring기반의 어플리케이션의 인증과 인가를 담당하는 프레임워크입니다.
    Spring Security는 Filter 기반으로 동작하기 때문에 Spring MVC와 분리되어 관리할 수 있고, Session-Cookie기반으로 동작합니다.
    또한 모든 요청에 대해 AuthenticationFilter 가 인증 및 권한 부여과정을 거친 후 Dispatcher Servlet으로 요청을 넘깁니다.
    다음은 Spring Security의 구조입니다.

<br>

![SpringSecurity](https://user-images.githubusercontent.com/29851990/204126595-38e0be3d-5bf4-48ed-8391-be3102567eaf.png)

<br>

동작방식을 다음과 같습니다.

<br>

    1. 사용자가 로그인을 시도합니다. (Http Request)
    2. Request는 AuthenticationFilter에 도달하게 되고, 이는 UsernamePasswordAuthenticationFilter에 (username, password)를 보내게 됩니다. 
    3. UsernamePasswordAuthenticationFilter에 도착하면 해당 클래스의 attempAuthentication가 동작하고 그 메서드에서 사용자 자격 증명을 기반으로한 UsernamePasswordAuthenticationToken을 생성합니다.
    4. 이어서 UsernamePasswordAuthenticationToken을 가지고 AuthenticationManager에게 인증을 진행하도록 위임합니다. (실제로는 AuthenticationManger 인터페이스를 구현한 ProviderManager)
    5. AuthenticationProvider의 목록으로 인증을 시도합니다.
    6. UserDetailService는 username기반의 UserDetails를 검색합니다.
    7. UserDetails를 이용해서 User 객체에 대한 정보를 검색합니다.
    8. User 객체의 정보를 UserDetails가 UserDetailsService에 전달함니다.
    9. 사용자의 인증이 성공하면 전체 인증정보를 리턴하고, 아니라면 AuthenticationException을 던집니다.
    10. AuthenicationManager가 인증객체를 Authentication Filter에 반환합니다.
    11. SecurityContext에 인증객체를 설정하고 마무리가 됩니다.

<br>

#### Security Session의 단점
    1. 대용량 트래픽에 대비한 scale-out이 어렵다. (세션 불일치문제)
    2. Session기반이기 떄문에 서버에 과부화가 올 수 있다.


<br>

#### JWT Token
    Stateless한 Http 프로토콜상에서 사용자의 인증과 권한에대한 정보를 암호화하여 Token형식으로 만들어 사용자에게 주는 방식입니다.
    JWT를 이용하면 따로 서버의 메모리에 저장 공간을 확보할 필요가 없습니다.
    또 서버가 토큰을 한번 클라이언트에게 보내주면 클라이언트는 토큰을 보관하고 있다가 요청을 보낼때마다 헤더에 토큰을 실어보내면 됩니다.
    마지막으로 쿠키를 사용할 수 없는 모바일 어플리케이션에는 JWT를 사용한 인증방식이 최적입니다.
    따라서 이번 프로젝트는 JWT 기반으로 구현하려합니다.

<br>

#### 의존성 부여
다음과 같이 build.gradle에 의존성을 부여해줍니다. (JWT가 최신이 아니라면 MVM Repository에서 찾아주시면 됩니다!)

    implementation 'org.springframework.boot:spring-boot-starter-security'
    implementation group: 'com.auth0', name: 'java-jwt', version: '3.19.2'

#### SecurityConfig

authorizeRequests : 권한과 그에따른 url을 정해줍니다.<br>
formLogin().disable() : 구현하고자 하는 서버의 디자인은 Rest Api 형태의 디자인이기 때문에 loginForm을 거치지않습니다.<br>
httpBasic : (Anthorization : {ID, PW}) 를 담아 보내는 방식입니다. 따라서 암호화가 안되있기 때문에 보안상 너무 위험합니다.<br>
MyCustomDsl : AbstractHttpConfigurer 에 거쳐야할 Filter들을 담습니다.<br>

    @Configuration
    @EnableWebSecurity
    public class SecurityConfig {
        @Autowired
        private UserRepository userRepository;

        @Autowired
        private CorsConfig corsConfig;

        @Bean
        public SecurityFilterChain filterChain(HttpSecurity http) throws Exception {
            http.csrf().disable()
                    .sessionManagement().sessionCreationPolicy(SessionCreationPolicy.STATELESS) //세션을 사용하지 않아 Stateless로 만들겠다.
                    .and()
                    .formLogin().disable()
                    .httpBasic().disable()
                    .apply(new MyCustomDsl()) // FilterChain으로 사용해야하므로 addFilter대신 apply사용 또한 authenticationManager를 사용해야하기 때문에
                    // 아래와같이 Custom으로 클래스를 만들어 사용
                    // beraer 방식 : 위의 Basic 방식과 다른 방식으로 Anthorization에 토큰을 담으므로 노출이 되도 위험부담이 적은 방식입니다.
                    .and()
                    .authorizeRequests()
                    .antMatchers("/user/**")
                    .access("hasRole('ROLE_USER') or hasRole('ROLE_REGISTER') or hasRole('ROLE_ADMIN')")
                    .antMatchers("/register/**")
                    .access("hasRole('ROLE_REGISTER') or hasRole('ROLE_ADMIN')")
                    .antMatchers("/admin/**")
                    .access("hasRole('ROLE_ADMIN')")
                    .anyRequest().permitAll();

            return http.build();
        }

        public class MyCustomDsl extends AbstractHttpConfigurer<MyCustomDsl, HttpSecurity> {
            @Override
            public void configure(HttpSecurity http) throws Exception {
                AuthenticationManager authenticationManager = http.getSharedObject(AuthenticationManager.class);
                http
                        .addFilter(corsConfig.corsFilter()) // cors 요청처리 // @CrossOrigin(인증 x), 시큐리티 필터에 등록 인증(o)
                        .addFilter(new JwtAuthenticationFilter(authenticationManager))
                        .addFilter(new JwtAuthorizationFilter(authenticationManager, userRepository));
            }
        }
    }

<br>

#### Cors

SOP(동일 출처 정핵)으로 인해 다른 출처의 리소스접근이 막힌 것을 풀어주는 "다른 출처간에 리소스를 공유할 수 있도록 해주는 정책"입니다.<br>
  
    @Configuration
    public class CorsConfig {

        @Bean
        public CorsFilter corsFilter(){
            UrlBasedCorsConfigurationSource source = new UrlBasedCorsConfigurationSource();
            CorsConfiguration config = new CorsConfiguration();
            config.setAllowCredentials(true); // 내 서버가 응답을 할 때, json을 자바스크립트에서 처리할 수 있게 할지를 설정
            config.addAllowedOrigin("*"); // 모든 ip에 응답을 허용하겠다.
            config.addAllowedHeader("*"); // 모든 header에 응답을 허용하겠다.
            config.addAllowedMethod("*"); // 모든 methode(get, post, put...)에 응답을 허용하겠다.

            source.registerCorsConfiguration("/api/**", config);
            return new CorsFilter(source);
        }
    }

<br>

#### JwtAuthenticationFilter.attemptAuthentication
    사용자가 로그인을 하게되면 SecurityFilterChain에 등록시킨 JwtAuthenticationFilter.attemptAuthentication(request, response)이 동작합니다.
    request로 온 username, password를 받아서 UsernamePasswordAuthenticationToken을 받고 정상인지 로그인을 시도합니다.
    authenticationManager로 로그인 시도하면 PrincipalDetailsService가 호출합니다.
    토큰을 이용해 PrincipalDetailsService의 loadUserByUsername() 함수를 실행시켜 DB에 있는 username과 password와 일치하는지 확인합니다.
    PrincipalDetails를 세션에 담고 (권한관리를 하기위함) authentication 객체가 session 영역에 저장됩니다.

<br>

#### JwtAuthenticationFilter.successfulAuthentication
    JWT 토큰을 만들어서 request를 보낸 사용자에게 jwt 토큰을 response 해줍니다.
    해당 프로젝트에서는 HMAC512 방식을 사용합니다.

<br>

#### JwtAuthorizationFilter.doFilterInternal
    인증이나 권한이 필요한 주소요청이 있을 때 해당 필터를 거칩니다.
    사용자가 보낸 JWT토큰을 확인해 정상적인 JWT Token이라면 Filter를 더 타게합니다.








