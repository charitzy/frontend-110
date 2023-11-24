<template>
  <div class="h-screen w-full flex justify-center items-center bg-[#332925]">
    <div class="h-full w-2/3">Hello</div>

    <div class="h-full w-1/3 flex items-center justify-center bg-slate-100">
      <form
        class="flex flex-col gap-4 h-2/3 w-96 overflow-y-auto justify-center"
        @submit.prevent="submitLogin"
      >
        <nuxt-img
          class="rounded-3xl"
          height="70"
          width="400"
          src="/f/263468/1563x1563/ef1c7a8b6b/onlineo-logo.png"
          alt="Onlineo Logo"
        />
        <label class="text-5xl font-bold">Login</label>
        <input
          required
          v-model="loginData.email"
          type="email"
          id="email"
          placeholder="Email"
          class="w-full bg-white/0 border-2 border-gray-400 text-sm rounded-lg p-2.5"
        />
        <input
          required
          v-model="loginData.password"
          type="password"
          id="password"
          placeholder="Password"
          class="w-full bg-white/0 border-2 border-gray-400 text-sm rounded-lg p-2.5"
        />
        <button
          class="h-10 w-11/12 bg-[#332925] text-white rounded-xl hover:scale-105 self-center"
          type="submit"
        >
          Login
        </button>
      </form>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";
import { useRouter } from "vue-router";

const router = useRouter();
const loginData = ref({ email: "", password: "" });

const submitLogin = async () => {
  try {
    const response = await fetch(
      "https://e3d2-143-44-193-32.ngrok-free.app/hay/public/api/login",
      {
        method: "POST",
        headers: {
          "Content-Type": "application/json",
          Accept: "application/json",
        },
        body: JSON.stringify({
          email: loginData.value.email,
          password: loginData.value.password,
        }),
      }
    );

    if (!response.ok) {
      const errorMessage = await response.text();
      console.error("Login failed with status:", response.status);
      console.error("Error message:", errorMessage);
      return;
    }

    const responseData = await response.json();
    console.log("Login successful:", responseData);

    // Redirect to another page or handle login success
    router.push("/dashboard");
  } catch (error) {
    console.error("Error during login:", error);
  }
};
</script>
