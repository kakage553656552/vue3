
<template>
  <div>
    <H1>hotfix</H1>
    <div>{{ n }}</div>
    <el-button type="primary" :icon="Plus" @click="btnClick">+</el-button>
    <HelloWorld :n="n" @setValue="setValue"></HelloWorld>
    <hr>
    <el-button>Default</el-button>
    <el-button loading type="primary">Primary</el-button>
    <el-button type="success">Success</el-button>
    <el-button type="info">Info</el-button>
    <el-button type="warning">Warning</el-button>
    <el-button type="danger">Danger</el-button>
    <el-button>中文</el-button>
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