<!-- Feed.vue -->
<template>
  <section class="section">
    <div class="container">
      
      <div class="columns is-multiline">
        <ReviewCard v-for="review in reviews" :key="review.id" :review="review" />
      </div>
    </div>
  </section>
</template>

<script>
import ReviewCard from './ReviewCard.vue';

export default {
  name: 'Feed',
  components: {
    ReviewCard
  },
  data() {
    return {
      reviews: [
        // Sample data
        {
          id: 1,
          image: 'https://www.foodiesfeed.com/wp-content/uploads/2023/06/burger-with-melted-cheese.jpg',
          userImage: 'https://images.pexels.com/photos/1043471/pexels-photo-1043471.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=2',
          dish: 'Spaghetti Carbonara',
          user: 'JohnDoe',
          restaurant: 'Italian Bistro',
          text: 'Delicious! Highly recommend.',
          orderAgain: true,
          date: '2024-05-01',
          portion: 4,
          taste: 4,
          value: 4,
          overall: 4.3
        },
        {
          id: 2,
          userImage: 'https://via.placeholder.com/48',
          dish: 'Margherita Pizza',
          user: 'JaneDoe',
          restaurant: 'Pizza Palace',
          text: 'Just okay. Could be better.',
          orderAgain: false,
          date: '2024-05-02',
          portion: 3,
          taste: 3,
          value: 3,
          overall: 3.0
        }
      ]
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
.level-item a {
  padding: 0.5rem;
}
.level-item a.is-active {
  color: #ff3860;
  border-bottom: 2px solid #ff3860;
}
</style>
