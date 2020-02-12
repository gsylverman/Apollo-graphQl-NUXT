<template>
  <div>
    Child
    <button @click="doSomething">click</button>
  </div>
</template>

<script>
import { eventBus } from './EventBus/EventBus'
export default {
  methods: {
    doSomething() {
      eventBus.$emit('someEvent', 'some data')
    }
  }
}
</script>
