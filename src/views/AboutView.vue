<template>
  <div class="container mt-5">
    <div class="row">
      <div class="col-md-4" v-for="review in reviews" :key="review.id">
        <div class="card mb-4 shadow-sm">
          <img :src="review.image" class="card-img-top" alt="Restaurant Image">
          <div class="card-body">
            <h5 class="card-title">{{ review.restaurantName }}</h5>
            <p class="card-text">{{ review.text }}</p>
            <div class="d-flex justify-content-between align-items-center">
              <div class="btn-group">
                <button type="button" class="btn btn-sm btn-outline-secondary">View</button>
                <button type="button" class="btn btn-sm btn-outline-secondary">Edit</button>
              </div>
              <small class="text-muted">{{ review.time }}</small>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'RestaurantReviews',
  data() {
    return {
      reviews: [
        {
          id: 1,
          restaurantName: 'Tio\'s Taco',
          image: 'https://via.placeholder.com/350x200?text=Pasta+Paradise',
          text: 'Great atmosphere and excellent tacos!',
          time: '3 mins ago'
        },
        {
          id: 2,
          restaurantName: 'Pasta Paradise',
          image: 'https://via.placeholder.com/350x200?text=Pasta+Paradise',
          text: 'Loved the creamy pasta here. Will come again!',
          time: '10 mins ago'
        }
        // Add more reviews as needed
      ]
    };
  }
}
</script>

<style scoped>
/* Add any specific styling you need here */
</style>

