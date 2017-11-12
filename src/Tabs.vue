<template>
  <ul :class="tabsClassName">
    <li v-for="tab in options"
        :class="[tabClassName, isActive(tab.value) ? activeTabClassName : '']"
        v-on:click="handleSelect(tab.value)"
    >
      {{ tab.text }}
    </li>
  </ul>
</template>

<script>
  export default {
    name: 'tabs',
    props: {
      options: {
        type: Array
      },
      tabsClassName: {
        type: String,
        default: 'tabs'
      },
      tabClassName: {
        type: String,
        default: 'tab'
      },
      activeTabClassName: {
        type: String,
        default: 'active'
      }
    },
    created: function () {
      if (this.options.length) {
        this.activeValue = this.options[0].value
        this.$emit('onChange', this.activeValue)
      }
    },
    data () {
      return {
        activeValue: ''
      }
    },
    methods: {
      handleSelect (value) {
        this.activeValue = value
        this.$emit('onChange', value)
      },
      isActive: function (value) {
        return this.activeValue === value
      }
    }
  }
</script>
