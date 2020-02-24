<template>
  <div class="wrapper">
    <h1>Task Manager</h1>
    <p>{{ state.messageOne }}</p>
    <p>{{ messageTwo }}</p>
    <Child :message="state.messageOne" @change-message="changeMessage" />
  </div>
</template>

<script lang="ts">
import { createComponent, reactive, ref, onMounted } from '@vue/composition-api'
import Child from '~/components/Child.vue'

export default createComponent({
  components: {
    Child
  },
  setup() {
    const state = reactive<{ messageOne: string }>({
      messageOne: 'is Reactive'
    })
    const messageTwo = ref<string>('is ref')

    const changeMessage = (message: string) => {
      state.messageOne = message
    }

    onMounted(() => {
      console.log('mounted')
    })

    return {
      state,
      messageTwo,
      changeMessage
    }
  }
})
</script>

<style>
.wrapper {
  margin: 0 auto;
  width: 960px;
}
</style>
