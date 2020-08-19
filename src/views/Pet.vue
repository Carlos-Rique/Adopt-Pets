<template>
  <div>
    <h1>Pet:</h1>
      <h2> {{ animal.name }} ({{ species }}) </h2>
      <p>Age: {{ animal.age }}</p>
      <p>Breed: {{ animal.breed }}</p>
  </div>
</template>

<script>
import { mapState } from 'vuex'
export default {
  props: ['species', 'id'],
  data () {
    return {
      animal: {}
    }
  },
  computed: {
    ...mapState([
      'cats',
      'dogs'
    ])
  },
  mounted () {
    // const animal = this[this.$route.params.species][this.$route.params.id]
    const animal = this[this.species.toLowerCase()][this.id]
    // console.log(animal)
    this.animal = animal
  }
}
</script>
