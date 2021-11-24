---
title: "component"
date: 2021-11-25
categories: vue  
---
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
