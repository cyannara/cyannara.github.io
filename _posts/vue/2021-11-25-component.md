---
title: "component"
date: 2021-11-25
categories: vue  
---

## 컴포넌트간의 데이터 전달방법

컴포넌트로 화면을 구성하게되면 컴포넌트마다 scope(유효범위)를 갖기 때문데 데이터를 공유할 수 없다.

* 상위 ↔ 하위 컴포넌트간의 전달
  * `props`, `emit` : props로 컴포넌트에 등록할 수 있는 커스텀 속성으로 하위 컴포넌트로 데이터 전달하고 emit 커스텀 이벤트 시스템으로 v-on 또는 @을 사용하여 하위 컴포넌트 인스턴스의 모든 이벤트를 수신
  ![props_emit](/img/vue/props_emit.png)
  * `provide , inject` : 부모 컴포넌트는 데이터 제공을 위해 provide 옵션을 사용하며, 자식 요소는 데이터 사용을 위해 inject 옵션을 사용

* 상위 → 하위 배포  
  * `slot` : 컨텐츠(html) 배포 API
  * `this.$root` 와 `this.$parent`

* 모든 컴포넌트가 공유
  * `EventBus`
  * `vuex`

## props

```js
//App.vue
<script>
import ComponentA from './components/ComponenA.vue'
export default {
  components: {   ComponentA  }
}
</script>

<template>
<div>
  <component-a msg='hi scott'></component-a>
</div>
</template>

<style scoped></style>
```

```js
//ComponentA.vue
<script>
export default {
    props: ['msg']
}
</script>
<template>
    <div>
        <h1>component A 입니다. {{msg}}</h1>
    </div>
</template>
```

## emit



## vuex store

* [참고사이트](https://vuex.vuejs.org/kr/){:target="_blank"}
* 전역 스토어. 메모리 기반의 저장소
* 애플리케이션 내 모든 컴포넌트들에게 중앙집중적인 저장소를 제공
* vue3의 컴포지션 API는 vuex의 역할을 대체가능하지만 하위호환성 및 개발자의 선호도로 인해 많이 사용되고 있음
* vuex는 Flux 아키텍쳐를 구현하는데 도움이 되는 라이브러리
  1. 컴포넌드들 간에 공유해야하는 데이터는 이를 사용하는 컴포넌트와 별도로 단위 위치에 보관
  2. 데이터는 읽기만 해야한다. 데이터를 변경하려면 store에 알리고 mutations 함수를 통해 변경해야한다.
  3. mutations는 synchronous(동기적)이어야 한다. 비동기적으로 발생한다면 데이터 추적이 힘들어짐
* vuex 설치

```js
npm install vuex@next
```
