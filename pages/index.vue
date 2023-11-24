<template>
  <div
    class="h-screen w-full relative bg-gradient-to-r from-white to-[#c4c8cc]"
  >
    <Navbar />
    <div
      class="h-screen w-full flex flex-row-reverse justify-center items-center"
    >
      <nuxt-img
        class=""
        format="webp"
        height="700"
        width="700"
        src="/f/263468/1563x1563/f7e6b76958/shop-phone.png"
      />
      <div class="w-[700px] flex flex-col gap-3">
        <h1 class="text-7xl font-bold text-black">
          Onlineo Your One Stop Shop for Buying and Selling
        </h1>
        <p class="text-2xl w-[600px] text-black">
          Onlineo is an online platform where people can buy or sell their
          products at a fast, secure, and reliable transactions.
        </p>
        <button
          class="h-10 w-32 rounded-full bg-[#464e5b] hover:bg-[#a1a6ab] hover:font-bold"
        >
          <NuxtLink to="/register" />
          Explore Shop
        </button>
      </div>
    </div>
    <TopCategories />
  </div>
</template>

<script setup></script>

<style lang="scss" scoped></style>
