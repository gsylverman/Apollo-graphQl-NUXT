<template>
  <div>
    app
    <div>{{ someWord }}</div>
    <some-comp></some-comp>
  </div>
</template>

<script>
import SomeComp from '~/components/SomeComp.vue'
import { eventBus } from '~/components/EventBus/EventBus.js'
export default {
  components: {
    SomeComp
  },
  data() {
    return {
      someWord: 'first'
    }
  },
  created() {
    eventBus.$on('someEvent', (p) => {
      this.someWord = p
    })
  }
}
</script>
