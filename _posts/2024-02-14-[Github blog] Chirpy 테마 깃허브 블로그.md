---
title: "[Github blog] Chirpy 테마 깃허브 블로그"
date: 2024-02-14 00:00:00 +0800
categories: [Blogging]
tags: [github, 블로그, chirpy, jekyll, chirpy 오류]
toc: true
---

# Chirpy 테마

앞선 글에서 `Chirpy-Starter` 를 활용하면 오류 없이 사용할 수 있다고 포스팅을 했었다. 그러나, `Starter`를 활용한 테마는 커스터마이징에 한계가 있었다. 이를 위해 기존의 테마를 다시 fork하여 블로그를 새로 단장했다. 이 말은 즉슨,, 다시 2일의 시간 동안 여러 오류들과 싸웠다는 말이다,,

## 👉 오류 1 - js does not exist

> js 파일 does not exist
> {: .prompt-danger }

이 오류는 ruby를 사용해 `jekyll server` 명령어를 입력하면 만날 수 있는 오류다. 로컬에서 사이트로 접속은 되지만, 이 오류가 발생한다면 야간모드로 전환이 안될 것이다. 또, 깃허브에 커밋도 되지 않는다.

이 오류를 해결하는데, 머리가 다 뽑히는 줄 알았다.

### 💡 해결 방법

1. ruby prompt에서 레파지토리를 clone한 폴더로 이동한다.

   ```
   cd '파일경로'
   ```

   ![alt text](/images/2024-02-14/ruby%20창.png)

2. `npm run build` 명령어 실행
3. js 파일이 잘 생성되었는지 확인한다.

---

## 👉 오류 2 - html does not exist

![alt text](/images/2024-02-14/html%20오류%20창.png)

깃허브에 push를 하면 Test Site에서 오류가 뜨면서 만날 수 있는 오류이다. 사실, 이 오류는 처음에 왜 발생하는지 조차 알지 못했다. 구글링에서도 나오지 않았기 때문이다.

### 💡 해결 방법

결론적으로 이 오류는 `_config.yml`의 홈페이지 url을 변경해주니 해결할 수 있었다.

내가 `chirpy-starter`를 처음에 사용하면서 `https://icekimchi.github.io` url을 이미 사용해서 다른 url을 사용하려고 했는데, 중간에 설정을 잘못 했는지 오류가 발생했다.

`_config.yml`의 url 넣는 칸을 `url: "https://icekimchi.github.io"`로 변경했더니 성공! 다른 분들도 자신이 설정한 url과 실제 배포하려는 사이트 url과 같은지 비교해보면 해결할 수 있을 것이다.
