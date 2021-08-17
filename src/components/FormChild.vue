<template>
  <form>
    <input class="border mb-2" :value="value.name" @input="onNameInput" />
    <input
      class="border"
      :value="value.commits"
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
  methods: {
    onNameInput(event) {
      const name = event.target.value
      console.log('name changed', name);
      this.$emit('input', {
        ...this.value,
        name,
      })
    },
    onCommitInput(event) {
      const commits = Number(event.target.value)
      console.log('commits changed', commits);
      this.$emit('input', {
        ...this.value,
        commits,
      })
    },
  },
}
</script>
