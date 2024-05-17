<template>
  <section class="section">
    <div class="container">
      <h1 class="title has-text-centered">Add a Review</h1>
      <form @submit.prevent="submitReview">
        <div class="field">
          <label class="label">Dish</label>
          <div class="control">
            <input class="input" type="text" v-model="dish" required>
          </div>
        </div>
        <div class="field">
          <label class="label">Restaurant</label>
          <div class="control">
            <input class="input" type="text" v-model="restaurant" required>
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
          <label class="label">Image URL</label>
          <div class="control">
            <input class="input" type="url" v-model="image" required>
          </div>
        </div>
        <div class="field">
          <label class="label">User Image URL</label>
          <div class="control">
            <input class="input" type="url" v-model="userImage" required>
          </div>
        </div>
        <div class="field">
          <label class="label">Username</label>
          <div class="control">
            <input class="input" type="text" v-model="user" required>
          </div>
        </div>
        <div class="columns">
          <div class="column">
            <div class="field">
              <label class="label">Portion</label>
              <div class="control">
                <input class="input" type="number" min="1" max="5" v-model="portion" required>
              </div>
            </div>
          </div>
          <div class="column">
            <div class="field">
              <label class="label">Taste</label>
              <div class="control">
                <input class="input" type="number" min="1" max="5" v-model="taste" required>
              </div>
            </div>
          </div>
          <div class="column">
            <div class="field">
              <label class="label">Value</label>
              <div class="control">
                <input class="input" type="number" min="1" max="5" v-model="value" required>
              </div>
            </div>
          </div>
          <div class="column">
            <div class="field">
              <label class="label">Overall</label>
              <div class="control">
                <input class="input" type="number" min="1" max="5" v-model="overall" required>
              </div>
            </div>
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
export default {
  name: 'AddReview',
  data() {
    return {
      dish: '',
      restaurant: '',
      text: '',
      orderAgain: true,
      image: '',
      userImage: '',
      user: '',
      portion: 3,
      taste: 3,
      value: 3,
      overall: 3
    }
  },
  methods: {
    submitReview() {
      // Logic to submit the review
      console.log({
        dish: this.dish,
        restaurant: this.restaurant,
        text: this.text,
        orderAgain: this.orderAgain,
        image: this.image,
        userImage: this.userImage,
        user: this.user,
        portion: this.portion,
        taste: this.taste,
        value: this.value,
        overall: this.overall,
        date: new Date().toISOString().split('T')[0]
      });
      this.clearForm();
    },
    clearForm() {
      this.dish = '';
      this.restaurant = '';
      this.text = '';
      this.orderAgain = true;
      this.image = '';
      this.userImage = '';
      this.user = '';
      this.portion = 3;
      this.taste = 3;
      this.value = 3;
      this.overall = 3;
    }
  }
}
</script>

<style scoped>
.form {
  max-width: 600px;
  margin: 0 auto;
}
</style>
