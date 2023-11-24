<template>
  <div class="font-Poppins">
    <NuxtPage />
  </div>
</template>
<script>
export default {
  setup() {
    // Destructure the response from useFetch
    const { data: csrf_token } = useFetch(
      "https://e3d2-143-44-193-32.ngrok-free.app/hay/public/api/csrf-token"
    );

    // Return the csrf_token
    return {
      csrf_token,
    };
  },
  head() {
    // Use the csrf_token variable
    return {
      meta: [
        {
          name: "csrf-token",
          content: this.csrf_token,
        },
      ],
    };
  },
};
</script>
