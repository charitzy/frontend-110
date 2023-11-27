<template>
  <div class="category-management">
    <div class="form-container">
      <h1>Category Management</h1>
      <div class="input-group">
        <input
          type="text"
          v-model="categoryName"
          placeholder="Enter category name"
          class="category-input"
        />
        <button @click="createCategory" class="create-btn">
          Create Category
        </button>
      </div>
    </div>

    <!-- Display saved category name -->
    <div v-if="categoryCreated" class="result-container">
      <p class="category-name">{{ categoryName }}</p>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from "vue";

let userToken = ref("");
const categoryName = ref("");
const categoryCreated = ref(false); // Reactive variable to track if category is created

// Retrieve the token when the component is mounted
onMounted(() => {
  userToken.value = localStorage.getItem("userToken");
});

const createCategory = async () => {
  try {
    const formData = new FormData();
    formData.append("category_name", categoryName.value);

    const response = await fetch(
      "https://9841-216-247-59-204.ngrok-free.app/it110/public/api/category",
      {
        method: "POST",
        headers: {
          Authorization: `Bearer ${userToken.value}`, // Use userToken.value
        },
        body: formData,
      }
    );

    const data = await response.json();
    if (response.ok) {
      alert("Category created successfully");
      console.log("Response:", data);
      categoryCreated.value = true; // Set categoryCreated to true after successful creation
    } else {
      alert(data.message || "Error creating category");
      categoryCreated.value = false;
    }
  } catch (error) {
    console.error("Error:", error);
    alert("An error occurred while creating the category.");
    categoryCreated.value = false;
  }
};
</script>
