---
layout: single
title: Vuex state
categories: web
---

state: data와 유사한 역할.
  mapState:
  // .vue file
  import {mapState} from 'vuex'
  computed:{
    ...mapState({name1:'내부 변수이름1',name2:'내부 변수이름2'})
    //...mapState(['내부 변수이름1','내부 변수이름2'])
    }.
getters: computed와 유사하게 반복되는 코드는 줄여준다. 다른 점은 this.로 불러오지 않고, 함수의 매개변수로 써주어야한다.
  mapGetters:
  // .vue file
  import {mapGetters} from 'vuex'
  computed:{
    ...mapGetters({name1:'getters 내부 함수1',name2:'getters 내부 함수2'})
    //...mapGetters(['getters 내부 함수1','getters 내부 함수2'])
    }.
    반복되는 $store.getters를 줄일 수 있다.
mutations: state 값 변화. 각각의 컴포넌트에서도 state를 바꿀 수 있다. 그렇다면 왜 mutation을 사용하는가? 그 이유는 컴포넌트에서 같은 기능을 하는 함수를 mutation내부에 만들고 실행시키기 위해서이다. 내부 함수는 (state,payload)를 받아야한다. 호출을 위해서는 this.$store.commit('mutations 함수 이름', 인자). 모든 기능이 동기로 작동을 하는 문제가 있다.
  mapMutations:
  // .vue file
  import {mapMutations} from 'vuex'
  methods:{
    ...mapMutations({name1:'mutations 내부 함수1',name2:'mutations 내부 함수2'})
    //...mapMutations(['mutations 내부 함수1','mutations 내부 함수2'])
    function1(){this.mutations 내부 함수1();}
    }.
    반복되는 $store.commit('')를 줄일 수 있다.
actions: 비동기 로직 처리. this.$store.dispatch(''). context를 인자로 받는 함수, context를 사용하지 않기 위해서는 ({commit}, payload)통해 해결할 수 있다.
  mapActions:
  // .vue file
  import {mapActions} from 'vuex'
  methods:{
    ...mapActions({name1:'actions 내부 함수1',name2:'actions 내부 함수2'})
    //...mapActions(['actions 내부 함수1','actions 내부 함수2'])
    function1(){this.actions 내부 함수1();}
    }.
    반복되는 $store.dispatch()를 줄일 수 있다.

###### 참고 사이트
[vuex에서 helper 사용하기](https://kamang-it.tistory.com/entry/Vue18vuex%EC%97%90%EC%84%9C-helper%EB%A5%BC-%EC%82%AC%EC%9A%A9%ED%95%98%EA%B8%B0mapState-mapMutations-mapActions-mapGetters)  
[Official-Vuex](https://vuex.vuejs.org/)  