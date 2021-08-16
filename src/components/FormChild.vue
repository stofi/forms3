<template>
  <form>
    <input class="border mb-2" :value="coder.name" @input="onNameInput" />
    <input
      class="border"
      :value="coder.commits"
      type="number"
      @input="onCommitInput"
      min="0"
      step="1"
    />
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
    this.coder = { ...this.value }
  },
  watch: {
    coder: {
      deep: true,
      handler(coder) {
        console.log('FormChild emits "input"', {coder})
        this.$emit('input', coder)
      },
    },
  },
  methods: {
    onNameInput(event) {
      const name = event.target.value
      console.log('name changed', name);
      this.$set(this.coder, 'name', name)
    },
    onCommitInput(event) {
      const commits = Number(event.target.value)
      console.log('commits changed', commits);
      this.$set(this.coder, 'commits', commits)
    },
  },
}
</script>
