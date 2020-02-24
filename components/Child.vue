<template>
  <div>
    <h2>child</h2>
    <p>{{ message }}</p>
    <button @click="upperCaseMessage">
      アッパーケースに変換
    </button>
  </div>
</template>

<script lang="ts">
import { createComponent, SetupContext } from '@vue/composition-api'

type Props = {
  message: string
}

export default createComponent({
  props: {
    message: {
      type: String,
      default: 'default value'
    }
  },
  setup(props: Props, context: SetupContext) {
    const upperCaseMessage = () => {
      context.emit('change-message', props.message.toUpperCase())
    }

    return {
      upperCaseMessage
    }
  }
})
</script>
