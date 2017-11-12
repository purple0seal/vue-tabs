<template>
  <div id="app">
    <tabs :options="tabs" v-on:onChange="handleTabChange"></tabs>
    {{ activeTab }}
  </div>
</template>

<script>
  import Tabs from '../../src/Tabs.vue'

  export default {
    name: 'app',
    components: { 'tabs': Tabs },
    data () {
      return {
        tabs: [
          {
            text: 'first',
            value: '1'
          },
          {
            text: 'second',
            value: '2'
          }
        ],
        activeTab: '',
      }
    },
    methods: {
      handleTabChange: function(value) {
        this.activeTab = value
      }
    }
  }
</script>
