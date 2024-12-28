<template>
  <div class="wrapper">
    <div
      class="asidebar flex flex-col bg-gray-900 text-white transition-all duration-300"
      :class="{ 'w-60': !isSidebarExpanded, 'w-16': isSidebarExpanded }"
    >
      <!-- Hamburger Button -->
      <div class="p-3 border-dashed border-b-2 border-light-blue-500">
        <button @click="toggleSidebar" class="focus:outline-none">
          <i
            class="fa-solid fa-bars"
            style="color: #ffffff; font-size: 24px"
          ></i>
        </button>
      </div>

      <!-- Sidebar Items -->
      <ul class="flex-1 mt-5 space-y-3">
        <li
          v-for="(item, index) in menuItems"
          :key="index"
          class="group flex items-center space-x-4 p-2 rounded-md hover:bg-gray-800 transition-all"
        >
          <!-- Icon -->
          <svg :class="item.icon" class="w-6 h-6 fill-current"></svg>
          <!-- Text (visible only when expanded) -->
           <router-link :to="item.path" class="flex items-center space-x-4">
            <span
            class="whitespace-nowrap transition-all duration-300"
            :class="{ hidden: isSidebarExpanded, block: !isSidebarExpanded }"
          >
            {{ item.text }}
          </span>
           </router-link>
          
        </li>
      </ul>

      <!-- Footer -->
      <div class="p-3">
        <div class="flex items-center justify-center">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            class="w-6 h-6"
            fill="currentColor"
            viewBox="0 0 24 24"
          >
            <path
              d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm0 18c-4.41 0-8-3.59-8-8s3.59-8 8-8 8 3.59 8 8-3.59 8-8 8zm0-14c-1.66 0-3 1.34-3 3s1.34 3 3 3 3-1.34 3-3-1.34-3-3-3zm0 12c-2.67 0-5.33-1.34-6.4-3.46.03-.68.68-1.24 1.39-1.24.6 0 1.1.37 1.31.91 1.16 2.08 4.06 2.09 5.22 0 .21-.54.71-.91 1.31-.91.71 0 1.36.56 1.39 1.24C17.33 16.66 14.67 18 12 18z"
            ></path>
          </svg>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isSidebarExpanded: false, // Default collapsed state
      menuItems: [
        { icon:"", text: "Dasboard", path: "/dashboard" },
        { icon: "icon-search", text: "Hospital Deapartment" },
        { icon: "icon-dashboard", text: "Doctor" },
        { icon: "icon-docs", text: "Patient" },
        { icon: "icon-products", text: "Doctor Schedule" },
        { icon: "icon-settings", text: "Patient Appointment" },
        { icon: "icon-messages", text: "Patient Case Studie" },
        { icon: "icon-messages", text: "Prescription" },
        { icon: "icon-messages", text: "Insurance" },
      ],
    };
  },
  methods: {
    toggleSidebar() {
      this.isSidebarExpanded = !this.isSidebarExpanded;
    },
  },
};
</script>

<style>
.wrapper {
  /* display: flex; */
  height: 100vh;
  width: 100%;
}

.asidebar {
  width: auto;
  height: 100vh;
  /* background-color: var(--secondary-color); */
}

/* Styling for expanded/collapsed sidebar */
.asidebar {
  transition: width 0.3s ease-in-out;
}

/* Sidebar Item - Icon Placeholder */
.icon-home {
  fill: white;
}
.icon-search {
  fill: white;
}
.icon-dashboard {
  fill: white;
}
.icon-docs {
  fill: white;
}
.icon-products {
  fill: white;
}
.icon-settings {
  fill: white;
}
.icon-messages {
  fill: white;
}

/* Icon adjustment for collapsed sidebar */
.asidebar.w-16 .icon-home,
.asidebar.w-16 .icon-search,
.asidebar.w-16 .icon-dashboard,
.asidebar.w-16 .icon-docs,
.asidebar.w-16 .icon-products,
.asidebar.w-16 .icon-settings,
.asidebar.w-16 .icon-messages {
  margin-left: auto;
}
</style>
