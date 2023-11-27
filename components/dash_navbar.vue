<template>
  <div class="h-16 w-full flex bg-black items-center justify-between fixed">
    <!-- Left side with the logo -->
    <div class="flex items-center px-4">
      <nuxt-link to="/">
        <nuxt-img
          class="cursor-pointer"
          format="webp"
          height="60"
          width="250"
          src="/f/263468/1563x1563/ef1c7a8b6b/onlineo-logo.png"
        />
      </nuxt-link>
    </div>

    <!-- Right side with menu items -->
    <div class="flex items-center">
      <!-- My Purchase -->
      <div class="px-4">
        <nuxt-link to="/purchase" class="text-white text-base hover:underline">
          My Purchase
        </nuxt-link>
      </div>

      <!-- English Language -->
      <div class="px-4">
        <nuxt-link to="/Selling" class="text-white text-base hover:underline">
          Start Selling
        </nuxt-link>
      </div>

      <!-- Help -->
      <div class="px-4">
        <nuxt-link to="/help" class="text-white text-base hover:underline">
          Help
        </nuxt-link>
      </div>

      <!-- Notifications -->
      <div class="px-4">
        <nuxt-link
          to="/notifications"
          class="text-white text-base hover:underline"
        >
          Notifications
        </nuxt-link>
      </div>

      <div class="px-4">
        <button @click="logout" class="text-white text-base">Log Out</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    logout() {
      console.log("Retrieved token:", localStorage.getItem("userToken"));
      const token = localStorage.getItem("userToken");
      if (!token) {
        console.error("No token found in localStorage");
        return;
      }

      fetch(
        "https://9841-216-247-59-204.ngrok-free.app/it110/public/api/logout",
        {
          method: "POST",
          headers: {
            "Content-Type": "application/json",
            Accept: "application/json",
            Authorization: `Bearer ${token}`,
          },
        }
      )
        .then((response) => {
          if (!response.ok) {
            throw new Error(`HTTP status ${response.status}`);
          }
          return response.json();
        })
        .then((data) => {
          console.log("Logged out:", data.message);
          localStorage.removeItem("userToken");

          // Redirect to the index.vue page
          this.$router.push({ name: "index" });
        })
        .catch((error) => {
          console.error("Logout error:", error.message);
        });
    },
  },
};
</script>
