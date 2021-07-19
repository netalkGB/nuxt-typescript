<template>
  <button @click="clickButton"><slot></slot></button>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  methods: {
    clickButton() {
      this.$emit('click')
    }
  }
})
</script>
