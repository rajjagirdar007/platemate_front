<template>
  <section class="section">
    <div class="container">
      <h3 class="title has-text-centered">Add a Review</h3>
      <form @submit.prevent="submitReview" class="form">
        <div class="field">
          <label class="label">Course</label>
          <div class="control">
            <div class="select">
              <select v-model="selectedCourse" @change="updateDishes">
                <option disabled value="">Select a course</option>
                <option v-for="course in courses" :key="course">{{ course }}</option>
              </select>
            </div>
          </div>
        </div>
        <div class="field" v-if="selectedCourse">
          <label class="label">Dish</label>
          <div class="control">
            <div class="select">
              <select v-model="dish">
                <option disabled value="">Select a dish</option>
                <option v-for="dish in meta.dishes[selectedCourse]" :key="dish">{{ dish }}</option>
              </select>
            </div>
          </div>
        </div>
        <div class="field">
          <label class="label">Review</label>
          <div class="control">
            <textarea class="textarea" v-model="text" required></textarea>
          </div>
        </div>
        <div class="field">
          <label class="label">Would you order it again?</label>
          <div class="control">
            <div class="select">
              <select v-model="orderAgain">
                <option :value="true">Yes</option>
                <option :value="false">No</option>
              </select>
            </div>
          </div>
        </div>
        <div class="field">
          <label class="label">Image</label>
          <div class="control">
            <input class="input" type="file" @change="onFileChange">
          </div>
        </div>
        <div class="columns is-multiline">
          <div class="column is-12">
            <label class="label">Portion</label>
            <star-rating v-model="portion" :star-size="30" :show-rating="false"></star-rating>
          </div>
          <div class="column is-12">
            <label class="label">Taste</label>
            <star-rating v-model="taste" :star-size="30" :show-rating="false"></star-rating>
          </div>
          <div class="column is-12">
            <label class="label">Value</label>
            <star-rating v-model="value" :star-size="30" :show-rating="false"></star-rating>
          </div>
          <div class="column is-12">
            <label class="label">Overall</label>
            <star-rating v-model="overall" :star-size="30" :show-rating="false"></star-rating>
          </div>
        </div>
        <div class="field is-grouped">
          <div class="control">
            <button class="button is-link" type="submit">Submit</button>
          </div>
          <div class="control">
            <button class="button is-link is-light" type="button" @click="clearForm">Cancel</button>
          </div>
        </div>
      </form>
    </div>
  </section>
</template>

<script>
import StarRating from 'vue-star-rating'

export default {
  name: 'AddReview',
  components: {
    StarRating
  },
  data() {
    return {
      selectedCourse: '',
      dish: '',
      text: '',
      orderAgain: true,
      image: null,
      portion: 3,
      taste: 3,
      value: 3,
      overall: 3,
      courses: ['Appetizers', 'Main', 'Dessert'],
      
      meta: {
        dishes: {
          Appetizers: [
            "Burger", "Pizza", "Pasta", "Salad", "Sandwich", "Soup", "Taco",
            "Sushi", "Steak", "Chicken", "Fish", "Shrimp", "Lobster", "Crab",
            "Scallop", "Oyster", "Clam", "Mussel", "Calamari", "Octopus", "Squid"
          ],
          Main: [
            "Burger", "Pork", "Beef", "Lamb", "Duck", "Turkey", "Goose", "Quail",
            "Venison", "Rabbit", "Buffalo", "Elk", "Boar", "Bear", "Moose", "Caribou",
            "Kangaroo", "Alligator", "Ostrich", "Emu", "Camel", "Alpaca", "Llama",
            "Horse", "Zebra", "Bison", "Snake", "Turtle"
          ],
          Dessert: [
            "Cake", "Frog", "Snail", "Cricket", "Grasshopper", "Ant", "Worm", "Fly",
            "Maggot", "Cockroach", "Beetle", "Wasp", "Bee", "Hornet", "Dragonfly",
            "Damselfly", "Butterfly", "Moth", "Mosquito", "Flea", "Bedbug", "Louse",
            "Tick", "Mite", "Spider", "Scorpion", "Centipede", "Millipede", "Crab",
            "Lobster", "Shrimp", "Crayfish", "Prawn", "Barnacle", "Krill", "Plankton",
            "Jellyfish", "Coral", "Sea anemone", "Sea cucumber", "Sea urchin", "Starfish",
            "Sand dollar", "Sea biscuit", "Sea sponge", "Sea squirt", "Tunicate", "Lancelet",
            "Ha"
          ]
        }
      }
    }
  },
  methods: {
    updateDishes() {
      this.dish = '';
    },
    submitReview() {
      // Logic to submit the review
      console.log(this.$data);
      this.clearForm();
    },
    clearForm() {
      Object.assign(this.$data, this.$options.data());
    },
    onFileChange(e) {
      const file = e.target.files[0];
      this.image = file ? URL.createObjectURL(file) : null;
    }
  }
}

</script>

<style scoped>
.form {
  max-width: 800px;
  margin: 0 auto;
}

.vue-star-rating{
  justify-content: center;
}

.star-rating {
  transition: transform 0.3s ease-in-out;
  
}

.star-rating:hover {
  transform: scale(1.1);
}
</style>

