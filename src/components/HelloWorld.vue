<template>
{{n}}
  <el-button type="primary" @click="updateValue">修改</el-button>
</template>
<script  lang="ts">
import { defineComponent,reactive,watch,ref } from 'vue'
export default defineComponent ({
  props: ['n'],
  setup(props,{emit}) {
    function updateValue() {
      emit('setValue',Math.floor(Math.random()*100))
    }
    return {updateValue}
  }
})
</script>