<template>
  <form>
    <input v-model="coder.name" />
    <input v-model="coder.commits" type="number" min="0" step="1" />
  </form>
</template>

<script>
export default {
  props: {
    value: {
      type: Object,
      default: () => ({}),
    },
  },
  data() {
    return {
      coder: {
        name: '',
        commits: 0,
      },
    }
  },
  mounted() {
    this.coder = this.value
  },
  watch: {
    value(newVal){
      this.$emit('input', newVal)
    }
  }
}
</script>
