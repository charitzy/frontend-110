<template>
  <div class="h-screen w-full flex justify-center items-center bg-[#332925]">
    <div class="h-full w-2/3">Hello</div>

    <div class="h-full w-1/3 flex items-center justify-center bg-slate-100">
      <form
        class="flex flex-col gap-4 h-2/3 w-96 overflow-y-auto justify-center"
        @submit.prevent="submitForm"
      >
        <nuxt-img
          class="rounded-3xl"
          height="70"
          width="400"
          src="/f/263468/1563x1563/ef1c7a8b6b/onlineo-logo.png"
          alt=""
        />
        <label class="text-5xl font-bold">Register</label>
        <input
          required
          v-for="data in userFields"
          :key="data.key"
          type="text"
          :id="data.id"
          :placeholder="data.placeholder"
          class="w-full bg-white/0 border-2 border-gray-400 text-sm rounded-lg p-2.5"
          v-model="userData[data.key]"
        />
        <button
          class="h-10 w-11/12 bg-[#332925] text-white rounded-xl hover:scale-105 self-center"
          type="submit"
        >
          Register
        </button>
      </form>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";
import { useRouter } from "vue-router";

const router = useRouter();

const userData = ref({
  username: "",
  first_name: "",
  last_name: "",
  email: "",
  password: "",
});

const userFields = [
  { id: "username", placeholder: "Username", key: "username" },
  { id: "first_name", placeholder: "First Name", key: "first_name" },
  { id: "last_name", placeholder: "Last Name", key: "last_name" },
  { id: "email", placeholder: "Email", key: "email" },
  { id: "password", placeholder: "Password", key: "password" },
  {
    id: "confirm_password",
    placeholder: "Confirm Password",
    key: "confirm_password",
  },
];

const submitForm = async () => {
  if (userData.value.password !== userData.value.confirm_password) {
    alert("Passwords do not match!");
    return;
  }

  try {
    const response = await fetch(
      "https://9841-216-247-59-204.ngrok-free.app/it110/public/api/register",
      {
        method: "POST",
        headers: {
          "Content-Type": "application/json",
          Accept: "application/json", // Specify that you accept JSON response
        },
        body: JSON.stringify({
          username: userData.value.username,
          first_name: userData.value.first_name,
          last_name: userData.value.last_name,
          email: userData.value.email,
          password: userData.value.password,
        }),
      }
    );

    if (!response.ok) {
      // Handle error responses here
      const errorMessage = await response.text();
      console.error("Registration failed with status:", response.status);
      console.error("Error message:", errorMessage);
      return;
    }

    // Registration was successful
    const responseData = await response.json();
    console.log("Registration successful:", responseData);

    router.push("/login");
  } catch (error) {
    console.error("Error during registration:", error);
  }
};
</script>
