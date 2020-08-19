<template>
  <div>
      <h1>{{ species }} for Adoption</h1>
      <b-table striped hover :items="pets">
        <template v-slot:cell(name)="data">
          <router-link :to="{name:'Pet', params: {id : data.index, species : species}}">
            {{data.value}}
          </router-link>
        </template>
      </b-table>
  </div>
</template>

<script>
export default {
  props: {
    species: String,
    pets: Array
  }
}
</script>
