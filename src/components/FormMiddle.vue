<template>
  <div class="space-y-4">
    <div v-for="(coder, index) in coders" :key="index" >
      <FormChild :value="coder" @input="onInput($event, index)" />
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
      console.log('FormMiddle recieves "input"', {coder, index});
      const clonedCoders = [...this.coders]
      clonedCoders[index] = coder
      this.$emit('input', clonedCoders)
      console.log('FormMiddle emits "input"', {clonedCoders});
    },
  },
}
</script>
