<template>
  <div class="dashboard-container">
    <!-- Header -->
    <header class="dashboard-header">
      <h1>Your Dashboard</h1>
    </header>

    <!-- Sidebar -->
    <aside class="dashboard-sidebar">
      <nav>
        <ul>
          <li><router-link to="/dashboard/home">Home</router-link></li>
          <li><router-link to="/dashboard/profile">Profile</router-link></li>
          <li><router-link to="/dashboard/settings">Settings</router-link></li>
          <!-- Add more navigation items here -->
        </ul>
      </nav>
    </aside>

    <!-- Main Content -->
    <main class="dashboard-content">
      <router-view></router-view>
      <!-- The content here will be replaced with the component associated with the route -->
    </main>
  </div>
</template>

<script>
export default {
  // Your script here
};
</script>

<style>
.dashboard-container {
  display: flex;
  height: 100vh;
}

.dashboard-header {
  width: 100%;
  padding: 10px;
  background-color: #333;
  color: white;
  text-align: center;
}

.dashboard-sidebar {
  width: 200px;
  background-color: #f4f4f4;
  padding: 20px;
}

.dashboard-sidebar ul {
  list-style-type: none;
  padding: 0;
}

.dashboard-sidebar ul li a {
  text-decoration: none;
  color: black;
}

.dashboard-content {
  flex-grow: 1;
  padding: 20px;
  background-color: #e9ecef;
}
</style>
