<template>
  <div class="h-16 w-full flex bg-black justify-around fixed">
    <nuxt-img
      class="px-3"
      format="webp"
      height="60"
      width="200"
      src="/f/263468/1563x1563/ef1c7a8b6b/onlineo-logo.png"
    />
    <div class="flex h-16 w-96 justify-around">
      <button class="text-lg hover:underline underline-offset-8">
        Products
      </button>
      <button class="text-lg hover:underline underline-offset-8">
        Marketplace
      </button>
      <button class="text-lg hover:underline underline-offset-8">
        About Us
      </button>
    </div>
    <div class="flex h-16 w-40 justify-around gap-3">
      <button class="font-bold">Login</button>
      <button
        class="h-8 w-28 bg-[#646b75] hover:bg-[#464e5b] rounded-full self-center font-bold"
      >
        <NuxtLink to="/register"> Register </NuxtLink>
      </button>
    </div>
  </div>
</template>

<script setup></script>
