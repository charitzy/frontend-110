<template>
  <div>
    <h1>My Purchases</h1>
    <ul>
      <li v-for="purchase in purchases" :key="purchase.id">
        {{ purchase.name }} - ${{ purchase.price }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      purchases: [
        { id: 1, name: "Product 1", price: 100 },
        { id: 2, name: "Product 2", price: 200 },
        // Add more purchase items here
      ],
    };
  },
};
</script>
