<template>
  <div class="header bg-gray-100 shadow-[4.0px_8.0px_8.0px_rgba(0,0,0,0.38)] overflow-hidden">
    <div class="content flex items-center justify-between p-4">
      <!-- Logo Section -->
      <div class="logo flex items-center space-x-4">
        <img 
          src="../assets/logo1.png" 
          alt="Logo" 
          class="w-12 h-12 rounded"
        >
        <p class="font-bold text-white text-sm leading-tight">
          Hospital Management <br>
          System
        </p>
      </div>
      <div class="search grow">
        <input 
          type="text" 
          placeholder="Search" 
          class="p-2 w-64 border border-gray-300 rounded-lg text-black"
        > 
      </div>

      <!-- Profile Section -->
      <div class="profile flex items-center flex-none w-20 ">
        <div class="img-profile flex items-center space-x-2">
          <img 
            src="../assets/profile1.jpg" 
            alt="Profile" 
            class="w-10 h-10 rounded-full border space-x-2" 
          >
          <!-- <div class="name">
            <i class="fa-solid fa-sort-down"></i>
        </div> -->
        </div>
      </div>
      
    </div>
  </div>
</template>

<script>
export default {
  name: "HeaderBar",
};
</script>
<style scoped>
.header {
  width: 100%;
  background-color: lightslategrey;
  height: 65px;
  padding: 15px;
  display: flex;
  align-items: center;
  justify-content: center;
  color: white;
}
.content {
  margin: 0px 5px;
}
</style>
