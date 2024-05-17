<template>
  <div class="menu">
    <h2 class="menu-title">Menu</h2>
    <div class="menu-items">
      <div v-for="(item, index) in menuItems" :key="index" class="menu-item">
        <img :src="item.image" alt="Menu item image" class="menu-item-image">
        <div class="menu-item-details">
          <h3 class="menu-item-name">{{ item.name }}</h3>
          <p class="menu-item-description">{{ item.description }}</p>
          <p class="menu-item-price">{{ item.price }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Menu',
  data() {
    return {
      menuItems: [
        {
          name: 'Item 1',
          description: 'Description of item 1',
          price: '$10',
          image: 'path/to/item1.jpg'
        },
        {
          name: 'Item 2',
          description: 'Description of item 2',
          price: '$12',
          image: 'path/to/item2.jpg'
        },
        // Add more menu items as needed
      ]
    }
  }
}
</script>

<style scoped>
.menu {
  padding: 20px;
}

.menu-title {
  font-size: 24px;
  text-align: center;
}

.menu-items {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}

.menu-item {
  margin: 10px;
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 5px;
  display: flex;
  align-items: center;
  max-width: 300px;
}

.menu-item-image {
  width: 80px;
  height: 80px;
  border-radius: 50%;
  margin-right: 20px;
}

.menu-item-details {
  flex: 1;
}

.menu-item-name {
  font-size: 18px;
}

.menu-item-description {
  margin-top: 5px;
  color: #666;
}

.menu-item-price {
  font-weight: bold;
  margin-top: 5px;
}
</style>
