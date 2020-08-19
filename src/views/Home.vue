<template>
  <div class="home-view-container">
    <h1>Adopt a new Best Friend</h1>
    <!-- {{getAllCats.length}}
    {{animalsCount}} -->
    <button @click="togglePetForm" class="btn btn-primary">Add a new Pet</button>

    <b-form @submit.prevent="submitPetForm" class="mt-4 form-home" v-if="showPetForm">
      <b-form-group id="input-group-2" label="Pet's Name:" label-for="input-2">
        <b-form-input
          id="input-2"
          type="text"
          v-model="form.name"
          placeholder="Enter name"
        ></b-form-input>
      </b-form-group>

      <b-form-group id="input-group-3" label="Specie:" label-for="input-3">
        <b-form-select
          id="input-3"
          v-model="form.species"
          :options="['cats','dogs']"
        ></b-form-select>
      </b-form-group>

      <b-form-group id="input-group-2" label="Age:" label-for="input-2">
        <b-form-input
          id="input-2"
          type="number"
          v-model="form.age"
          placeholder="0"
        ></b-form-input>
      </b-form-group>

      <b-button type="submit" variant="primary">Submit</b-button>
      <b-button type="reset" variant="danger">Reset</b-button>
    </b-form>

  </div>
</template>

<script>
import { mapActions, mapGetters } from 'vuex'
export default {
  name: 'Home',
  data () {
    return {
      form: {
        name: '',
        species: '',
        age: null
      },
      showPetForm: false
    }
  },
  computed: {
    ...mapGetters([
      'animalsCount',
      'getAllCats'
    ])
  },
  methods: {
    ...mapActions([
      'addPet'
    ]),
    togglePetForm () {
      this.showPetForm = !this.showPetForm
    },
    submitPetForm () {
      console.log(this.form)
      const { name, species, age } = this.form
      const payload = {
        species,
        pet: {
          name,
          age
        }
      }
      this.addPet(payload)
      this.form = {
        name: '',
        species: '',
        age: null
      }
    }
  }
}

</script>

<style scoped>
  .form-home{
    border: dotted 1px darkgrey;
    padding: 10px 5px;
    border-radius: 5px;
  }
</style>
