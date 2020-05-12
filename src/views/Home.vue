<template>
  <div class="home-view-container">
    <h1>Adopt a new pet</h1>
    {{ getAllCats.length }} Cats <br>
    {{ animalsCount }} Pets<br>
    <button @click="togglePetForm" class="btn btn-primary">Add New Pet</button>
    <b-form @submit.prevent="handleSubmit" v-if="showPetForm"><br>
      <img v-if="showImg" :src="formData.imgSrc" width="80px" height="80px"/>
      <b-form-group id="pet_name" label="Pet Name:" label-for="input-2">
        <b-form-input
          id="name"
          v-model="formData.name"
          required
          placeholder="Enter name"
        ></b-form-input>
      </b-form-group>

      <b-form-group id="pet_species" label="Species:" label-for="input-3">
        <b-form-select
          id="species"
          v-model="formData.species"
          :options="['cats', 'dogs']"
          required
        ></b-form-select>
      </b-form-group>

      <b-form-group id="pet_age" label="Pet Age:" label-for="input-2">
        <b-form-input
          id="age"
          v-model="formData.age"
          type="number"
          required
          placeholder="Enter age"
        ></b-form-input>
      </b-form-group>

      <b-form-group id="price" label="Pet Price" label-for="price">
        <b-form-input
          id="price"
          v-model="formData.price"
          type="number"
          required
          placeholder="Enter Price in $"
        ></b-form-input>
      </b-form-group>
      <b-form-group id="img-src" label="Pet Image: " label-for="img">
        <b-form-input
          id="img"
          @change="toggleShowImg"
          v-model="formData.imgSrc"
          type="text"
          required
          placeholder="Enter Image address"
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
  data: () => {
    return {
      showPetForm: false,
      formData: {
        name: '',
        age: null,
        species: null,
        imgSrc: '',
        price: null
      },
      showImg: false
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
    handleSubmit () {
      const { species, name, age, imgSrc, price } = this.formData
      const payload = {
        species,
        pet: {
          name,
          age,
          imgSrc,
          price
        }
      }
      this.addPet(payload)

      // reset
      this.formData = {
        name: '',
        age: null,
        species: null,
        imgSrc: '',
        price: null
      }
    },
    toggleShowImg () {
      this.showImg = !this.showImg
    }
  }
}
</script>
