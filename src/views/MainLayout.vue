<template>
    <div class="wrapper">
      <div class="container">
        <div class="asidebar">
          <AsideBar />
        </div>
        <div class="main-body bg-gray-100 transition-all duration-300"
        :class="{ '': !isSidebarExpanded, 'ml-100': isSidebarExpanded }">
          
            <div class="header-bar">
              <HeaderBar></HeaderBar>
            </div>
          
          <div class="body "
          
		>
            <router-view />
          </div>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  import "../main.js";
  import AsideBar from '@/components/AsideBar.vue';
import HeaderBar from '@/components/HeaderBar.vue';
  
  export default {
    name: 'MainLayout',
    components: { 
      AsideBar,
        HeaderBar 
    },
    methods: {
    toggleSidebar() {
      this.isSidebarExpanded = !this.isSidebarExpanded;
    },
  },
  };
  </script>
  
  <style>
@import '../main.css';
.wrapper {
  width: 100%;
  height: auto;
  display: flex;
}
.container{
  max-width: 100% !important;
  display: flex;
  flex-direction: row;
}
.body {
  overflow: auto;
  width: auto;
}
.main-body{
  width: 100%;
  max-width: 100%;
}
</style>

  