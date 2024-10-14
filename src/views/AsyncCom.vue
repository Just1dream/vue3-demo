<template>
  <div>

    <button @click="changeCom">AsyncCom</button>
    <component :is="currentCom" :key="currentCom.name" />
  </div>
</template>

<script lang="ts" setup>
import { defineAsyncComponent, ref } from 'vue'

let currentName = 'AsyncCom'


const AsyncCom = defineAsyncComponent(() => import('./test.vue'))


const AsyncCom2 = defineAsyncComponent(() => import('./test2.vue'))

const currentCom = ref(AsyncCom2)


const changeCom = () => {

  if (currentName === 'AsyncCom') {
    currentName = 'AsyncCom2'
    currentCom.value = AsyncCom2
  } else {
    currentName = 'AsyncCom'
    currentCom.value = AsyncCom
  }
}

</script>

<style lang="scss" scoped></style>