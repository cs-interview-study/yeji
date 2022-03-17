# SSR & CSR

[✔️블로그 링크](https://whwl.tistory.com/283)

## 🗨️ SSR(Server Side Rendering)

<img src="https://blog.kakaocdn.net/dn/dvCfyw/btrwgRq8Pu8/MxJKRkpeMO5tykf1wIRpi1/img.png" alt="img" style="zoom:50%;" />

전통적인 MPA(Multi Page Application)의 렌더링 방식, 브라우저(클라이언트)가 데이터 요청 시 브라우저 -> 프론트 서버 -> 백엔드 서버 -> 데이터베이스를 거쳐 데이터베이스에서 HTML 문서를 가져온 후 브라우저에 화면을 렌더링 하는 방식이다.

클라이언트 측에서 페이지 이동 및 클릭으로 요청이 발생할 때마다 서버에 요청하여 전체 HTML 문서를 다시 가져오기 때문에 변화하지 않는 부분까지도 다시 렌더링 되고, 잦은 서버 요청으로 부하가 일어나는 등의 비효율성을 초래한다.

SSR은 첫 화면에서 기존 데이터가 존재하는 HTML 문서가 있기 때문에 검색 엔진이 색인을 생성하고 크롤링할 수 있어 SEO에 좋다. 사용자 인터랙션이 많지 않은 정적 사이트(특히 텍스트 기반)에 적합하다.



`SSR의 장점`

👉 검색 엔진이 사이트를 크롤링 할 수 있어 SEO가 좋다.

👉 빠른 초기 로딩 속도

👉 정적 사이트에 적합

`SSR의 단점`

👉 잦은 요청으로 서버 과부하

👉 일부 리렌더링 X -> 전체 페이지를 리렌더링 O -> 화면 깜빡임이 있다.

👉 사이트 내 사용자 인터랙션이 풍부하지 않다.





## 🗨️ CSR(Client Side Rendering)

<img src="https://blog.kakaocdn.net/dn/41nKb/btrwb3y7sQX/0QakAzlpuER1HdwP77Q0B1/img.png" alt="img" style="zoom:50%;" />

리액트, 뷰 등 주로 SPA(Single Page Application)에서 쓰이는 렌더링 방식으로 사이트 첫 화면에서 데이터를 제외하고 나머지 요소들을 프론트 서버에서 받아온다. 데이터를 제외한 코드들의 번들을 js 파일 하나로 받아오기 때문에 처음에 해당 파일을 받아오는데 시간이 소요된다. 따라서 초기 렌더링 시 사용자 측에서는 로딩 화면을 마주하는 시간이 생기게 된다. 초기 렌더링 속도는 느리지만 이후 필요한 데이터만을 백엔드 서버에 요청하여 받아와 갱신하기 때문에 향후 데이터 갱신 시에는 SSR 방식과 비교했을 때 속도가 더 빠르게 나타난다.



특히 초기 HTML 문서에 데이터가 없기 때문에 검색 엔진이 크롤링 시 빈페이지로 착각하여 SEO(Search Engine Optimization)에 취약하다는 단점이 있다. 구글의 검색봇은 자바스크립트를 실행할 줄 알아서 CSR이 SEO에 취약한 점을 보완해준다고 하지만 아직까지는 그 효과가 크지 않다고 한다.



`CSR의 장점`

👉 화면 깜빡임이 없다

👉 활발한 사용자 인터랙션

👉 초기 로딩 이후 빠른 리렌더링

👉 서버 요청 분산

`CSR의 단점`

👉 SEO 취약

👉 자바스크립트 파일을 모두 다운 받은 후 화면을 렌더링 하기 때문에 초기 로딩 시 시간이 걸린다.





## 🗨️ CSR을 보완해주는 Next.js

Next.js 프레임워크를 사용하여 첫 페이지를 SSR 방식으로 받아와 렌더링하여 SEO 문제를 보완하고 그 다음 페이지 전환부턴 CSR 방식을 적용하여 서버 과부하를 줄이고 빠른 렌더링이 가능해진다. 페이지에 제공할 데이터, 서비스에 따라 SSR 또는 CSR 방식을 자유롭게 적용할 수 있다.

<img src="https://blog.kakaocdn.net/dn/caojTH/btrwivnyYmR/tTT0afV9IUgpZIR1fK1zq0/img.png" alt="img" style="zoom:50%;" />



## 🗨️ 결론 

어떤 렌더링 방식이 효율적이라고 정해진 답은 없으며, 각각의 장단점을 비교한 후 서비스의 성격에 따라 SSR / CSR / SSG / SSR + CSR을 선택할 수 있다.

