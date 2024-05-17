<!-- ReviewCard.vue -->
<template>
  <div class="column is-full-mobile is-one-third-tablet">
    <div class="card">
      <div v-if="review.image" class="card-image">
        <figure class="image is-4by3">
          <img :src="review.image" :alt="`Image of ${review.dish}`">
        </figure>
      </div>
      <div class="card-content">
        <div class="media">
          <div class="media-left">
          </div>
          <div class="media-content has-text-centered">
            <p class="title is-4">{{ review.user }}</p>
            <p class="subtitle is-6">{{ review.dish }} @{{ review.restaurant }}</p>
          </div>
        </div>
        <div class="content">
          {{ review.text }}
          <br>
          <strong>Would order again:</strong> {{ review.orderAgain ? 'Yes' : 'No' }}
          <br>
          <time :datetime="review.date">{{ review.date }}</time>
          <div class="ratings">
            <div class="rating-item">
              <strong>Portion:</strong>
              <span v-html="generateStars(review.portion)"></span>
            </div>
            <div class="rating-item">
              <strong>Taste:</strong>
              <span v-html="generateStars(review.taste)"></span>
            </div>
            <div class="rating-item">
              <strong>Value:</strong>
              <span v-html="generateStars(review.value)"></span>
            </div>
            <div class="rating-item">
              <strong>Overall:</strong>
              <span v-html="generateStars(review.overall)"></span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ReviewCard',
  props: {
    review: Object
  },
  methods: {
    generateStars(rating) {
      let stars = '';
      for (let i = 1; i <= 5; i++) {
        if (i <= rating) {
          stars += '<i class="fas fa-star has-text-warning"></i>';
        } else if (i <= Math.ceil(rating)) {
          stars += '<i class="fas fa-star-half-alt has-text-warning"></i>';
        } else {
          stars += '<i class="far fa-star"></i>';
        }
      }
      return stars;
    }
  }
}
</script>

<style scoped>
.card {
  margin-bottom: 1.5rem;
}
.card-content {
  padding: 1rem;
}
.media-content {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  text-align: center;
}
.ratings {
  display: flex;
  flex-direction: column;
  align-items: center; /* Center items horizontally */
  justify-content: center; /* Center items vertically */
  margin-top: 1rem;
}
.rating-item {
  display: flex;
  align-items: center; /* Align text and stars vertically */
  margin-bottom: 0.5rem;
  text-align: center; /* Center text */
}
.has-text-warning {
  color: yellow;
}
</style>
