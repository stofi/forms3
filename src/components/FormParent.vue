<template>
  <div>
    <FormMiddle v-model="coders" />
    <pre>{{ coders }}</pre>
  </div>
</template>

<script>
import FormMiddle from '@/components/FormMiddle.vue'

export default {
  components: {
    FormMiddle
  },
  data() {
    return {
      coders: [
        {
          name: 'Krystof',
          commits: 0,
        },
        {
          name: 'Tiep',
          commits: 2,
        },
        {
          name: 'Jaromir',
          commits: 3,
        },
        {
          name: 'Petr',
          commits: 3,
        },
      ],
    }
  },
  watch: {
    coders(coders) {
      console.log('FormParent "coders" watcher', {coders});
    }
  }
}
</script>
