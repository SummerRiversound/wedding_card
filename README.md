# Wedding Card
해당 Repository 주인의 결혼식 `(12월 11일)` 모바일 청접장입니다

개인적으로 편하게 사용하거나 수정하셔도 상관없으나 사진을 반드시 교체하여 사용해주시고, 사진을 절대 도용하지 말아주시기 바랍니다   

[DEMO Page](https://summerriversound.github.io/pre_intro/WeddingCard/ "청첩장데모페이지")

---

## 사용
.env 파일을 수정하여 환경변수값을 변경합니다

```
VUE_APP_WEDDING_NAME= 타이틀 // ex) 이하은·문미영 결혼합니다
VUE_APP_WEDDING_DAY= 결혼날짜 // ex) 2020년 12월 11일
VUE_APP_DEPOLY_URL= 배포주소 // ex) https://summerriversound.github.io/
VUE_APP_THOMNAIL_URL= 카톡공유용 썸네일주소 ex) static/img/DSC03779.d568e15f.jpg
```
아래 위치에 있는 사진파일들을 변경해줍니다
```
/public/static/img
```

이후 일반 Vue js프로젝트와 똑같은 방식으로 빌드하고 배포하시면됩니다

---

``Tech stack: VueJS 2, Vuetify``

---


## Project setup
```
yarn install
```

### Compiles and hot-reloads for development
```
yarn serve
```

### Compiles and minifies for production
```
yarn build
```

### Lints and fixes files
```
yarn lint
```



### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).
