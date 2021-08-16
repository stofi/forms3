<template>
  <div>
    <div v-for="(coder, index) in coders" :key="index">
      <FormChild :valuel="coder" @input="onInput($event, index)" />
    </div>
  </div>
</template>

<script>
import FormChild from '@/components/FormChild.vue'

export default {
  components: { FormChild },
  model : {
    prop: 'coders',
  },
  props: {
    coders: {
      type: Array,
      default: ()=>[]
    }
  },
  methods: {
    onInput(coder, index) {
      const clonedCoders = JSON.parse(JSON.stringify(this.coders))
      clonedCoders[index] = coder
      this.$emit('input', clonedCoders)
    },
  },
}
</script>
