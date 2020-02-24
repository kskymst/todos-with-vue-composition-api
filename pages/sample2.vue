<template>
  <div class="wrapper">
    <h1>other types</h1>
    <p>{{ count }}</p>
    <button @click="increment">
      up
    </button>
  </div>
</template>

<script lang="ts">
import { createComponent, ref } from '@vue/composition-api'
const useCounter = () => {
  const count = ref(0)
  const increment = () => {
    count.value++
  }
  return { count, increment }
}
export default createComponent({
  setup() {
    const { count, increment } = useCounter()
    return { count, increment }
  }
})
</script>

<style>
.wrapper {
  width: 960px;
  margin: 40px auto 0;
}
</style>
