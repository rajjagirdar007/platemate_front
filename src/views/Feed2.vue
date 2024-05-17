<template>
  <section class="section">
    <div class="container">
      <!-- Search and Filter Toggle on Mobile -->
      <button class="button is-info is-rounded is-hidden-desktop" @click="showFilters = !showFilters" style="position: fixed; bottom: 20px; right: 20px; z-index: 100;">
        <i class="fas fa-filter"></i>
      </button>

      <!-- Search Bar and Filters -->
      <div class="box" :class="{'is-hidden-mobile': !showFilters}">
        <div class="field">
          <p class="control has-icons-left">
            <input class="input" type="text" placeholder="Search reviews..." v-model="searchQuery">
            <span class="icon is-small is-left">
              <i class="fas fa-search"></i>
            </span>
          </p>
        </div>
        
        <div class="field is-grouped is-grouped-multiline">
          <div class="control">
            <div class="select">
              <select v-model="filter.course" @change="updateDishes">
                <option value="">All Courses</option>
                <option v-for="course in courses" :key="course">{{ course }}</option>
              </select>
            </div>
          </div>
          <div class="control" v-if="filter.course">
            <div class="select">
              <select v-model="filter.dish" @change="applyFilters">
                <option value="">All Dishes</option>
                <option v-for="dish in dishes" :key="dish">{{ dish }}</option>
              </select>
            </div>
          </div>
          <div class="control">
            <div class="select">
              <select v-model="filter.orderAgain" @change="applyFilters">
                <option value="">Order Again?</option>
                <option :value="true">Yes</option>
                <option :value="false">No</option>
              </select>
            </div>
          </div>
        </div>
      </div>

      <!-- Reviews List -->
      <div class="columns is-multiline">
        <ReviewCard v-for="review in filteredReviews" :key="review.id" :review="review" />
      </div>

      <!-- Infinite Scroll Loader -->
      <div v-if="loading" class="has-text-centered">
        <button class="button is-loading is-fullwidth">Loading...</button>
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
      searchQuery: '',
      filter: {
        course: '',
        dish: '',
        orderAgain: ''
      },
      courses: ['Appetizers', 'Main', 'Dessert'],
      dishes: [],
      reviews: [
        {
          id: 1,
          image: 'https://example.com/image1.jpg',
          userImage: 'https://example.com/user1.jpg',
          course: 'Main Course',
          dish: 'Spaghetti Carbonara',
          restaurant: 'Italian Bistro',
          text: 'Delicious! Highly recommend.',
          orderAgain: true,
          date: '2024-05-01',
          time: '12:00',
          portion: 4,
          taste: 4,
          value: 4,
          overall: 4.3
        },
        {
          id: 2,
          image: 'https://example.com/image2.jpg',
          userImage: 'https://example.com/user2.jpg',
          course: 'Appetizers',
          dish: 'Bruschetta',
          restaurant: 'Italian Bistro',
          text: 'Could use more garlic, but still tasty!',
          orderAgain: false,
          date: '2024-05-02',
          time: '14:30',
          portion: 3,
          taste: 3,
          value: 2,
          overall: 2.8
        },
        {
          id: 3,
          image: 'https://example.com/image3.jpg',
          userImage: 'https://example.com/user3.jpg',
          course: 'Dessert',
          dish: 'Cheesecake',
          restaurant: 'Cheesecake Factory',
          text: 'Best cheesecake ever!',
          orderAgain: true,
          date: '2024-05-03',
          time: '16:00',
          portion: 5,
          taste: 5,
          value: 5,
          overall: 5
        },
        // Add more reviews as needed
      ],
      filteredReviews: [],
      loading: false,
      showFilters: false,
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
    };
  },
  created() {
    this.applyFilters();
    window.addEventListener('scroll', this.handleScroll);
  },
  destroyed() {
    window.removeEventListener('scroll', this.handleScroll);
  },
  methods: {
    handleScroll() {
      let bottomOfWindow = document.documentElement.scrollTop + window.innerHeight === document.documentElement.offsetHeight;
      if (bottomOfWindow) {
        this.loadMore();
      }
    },
    loadMore() {
      this.loading = true;
      // Simulated loading delay
      setTimeout(() => {
        // This is where you would typically add more data from your backend
        this.loading = false;
      }, 2000);
    },
    updateDishes() {
      this.filter.dish = '';
      this.dishes = this.meta.dishes[this.filter.course] || [];
      this.applyFilters();
    },
    applyFilters() {
      this.filteredReviews = this.reviews.filter(review => {
        return (
          (!this.searchQuery || review.text.toLowerCase().includes(this.searchQuery.toLowerCase()) || review.dish.toLowerCase().includes(this.searchQuery.toLowerCase())) &&
          (!this.filter.course || review.course === this.filter.course) &&
          (!this.filter.dish || review.dish === this.filter.dish) &&
          (this.filter.orderAgain === '' || review.orderAgain === this.filter.orderAgain)
        );
      });
    }
  },
  watch: {
    searchQuery: 'applyFilters',
    filter: {
      handler: 'applyFilters',
      deep: true
    }
  }
};
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
.container {
  padding: 3rem 1.5rem;
}
.section {
  padding: 0 !important;
}
.is-rounded {
  border-radius: 50%;
}
</style>
