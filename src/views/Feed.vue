<template>
<div>
    <img src="/assets/img/fijita.jpeg" class="card-img-top" style="height: 230px;"/> 
    <article class="media">
        <figure class="media-left">
            <p class="image is-64x64">
                <img src="/assets/img/avatar.png" />
            </p>
        </figure>
        <div class="media-content">
            <div class="content">
                <p>
                    <strong>John Smith</strong> <small>ate</small> <strong>Tapas</strong> <small> at </small> <strong>Tio's Taco</strong> <small>31m</small>
                    <br />  
                    <article class="message is-success">
                        <div class="message-header">
                            <div class="columns is-mobile is-multiline is-centered">
                                <div class="column is-narrow">
                                    <p>
                                        Overall = 4.0<br />
                                        Would you Order Again? Yes.
                                    </p>
                                </div>
                            </div>
                        </div>
                        <div class="message-body">
                            The chicken burrito's portion was satisfying, but the overwhelming amount of queso made it slightly soggy, affecting the overall taste. While it offered good value for the price, the seasoning leaned too much on the salty side, overpowering the other flavors and leaving the dish a bit unbalanced.
                        </div>
                    </article>
                </p>
            </div>
            <nav class="level is-mobile">
                <div class="level-left">
                    <a class="level-item">
                        <span class="icon is-small"><i class="fas fa-reply"></i></span>
                    </a>
                    <a class="level-item">
                        <span class="icon is-small"><i class="fas fa-retweet"></i></span>
                    </a>
                    <a class="level-item">
                        <span class="icon is-small"><i class="fas fa-heart"></i></span>
                    </a>
                </div>
            </nav>
        </div>
    </article>
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
          text: 'Loved the creamy pasta here. Will come againdsfhssfsdf!',
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

