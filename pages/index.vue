<template>
  <div>
    <nt-button @click="increment">TEST</nt-button>
    <div>{{ count }}</div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import { createNamespacedHelpers } from 'vuex'
import NtButton from '@/components/NtButton'

const { mapActions, mapGetters } = createNamespacedHelpers('counter')

export default Vue.extend({
    components: {
      NtButton
    },
    mounted() {
      console.log('mounted')
    },
    methods: {
      increment() {
        console.log('increment')
        this.add()
      },
      ...mapActions({
        add: 'increment' // this.add()でactionのincrement呼び出す
      })
    },
    computed: {
      ...mapGetters({
        count: 'getCount'
      })
    }
})
</script>
