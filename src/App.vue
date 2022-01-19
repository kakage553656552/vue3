
<template>
  <div>
    <div>{{ n }}</div>
    <button @click="btnClick">+</button>
    <HelloWorld :n="n" @setValue="setValue"></HelloWorld>
  </div>
</template>
<script  lang="ts">
import { defineComponent,reactive,watch,ref } from 'vue'
import HelloWorld from './components/HelloWorld.vue'
export default defineComponent ({
  components: {
    HelloWorld
  },
  name: 'App',
  setup() {
    const state = reactive({ num: 10 })
    let n = ref(1)
    function btnClick() {
      n.value++
    }
    const stop = watch(()=>n.value,(val,old)=>{
      console.log(val,old);
    })
    function setValue(val) {
      n.value = val
    }
    return { state,btnClick,n,setValue }
  }
})
</script>