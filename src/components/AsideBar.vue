<template>
  <div class="wrapper overflow-hidden">
    <!-- Sidebar -->
    <div
      class="asidebar flex flex-col text-white transition-all duration-300 "
      :class="{ 'w-60': isSidebarExpanded, 'w-16': !isSidebarExpanded }"
    >
      <!-- Hamburger Button -->
     <div class="header-bar shadow-[4.0px_8.0px_8.0px_rgba(0,0,0,0.38)] p-3 flex items-center justify-between border-dashed border-b-2 border-light-blue-500 ">
      <div class="logo flex items-center justify-between ">
        <div class="logo-inner ">
         <button @click="toggleSidebar" class="focus:outline-none">
          <p :class="{'text-4xl': isSidebarExpanded, 'text-5xl,transition-all duration-300': !isSidebarExpanded}" class=" font-bold">HMS</p>
         </button>
        </div>
        <!-- <div class="text-logo ">
          <p style="font-size: 10px;">HMS</p>
          <p style="font-size: 7px;">Hospital Mangement</p>
        </div> -->
      </div>
      <!-- <div class="buger">
        <button @click="toggleSidebar" class="focus:outline-none">
          <i
            class="fa-solid fa-bars"
            style="color: #ffffff; font-size: 24px"
          ></i>
        </button>
      </div> -->
      
     </div>
     <div class="status text-center mt-5 border-dashed border-b-2 border-light-blue-500 "
      :class="{ 'hidden': !isSidebarExpanded, 'block': isSidebarExpanded }">
      <div class="profile text-center"
     >
        <img style="margin: auto" class="w-20 h-20 rounded-full border"  src="../assets/profile1.jpg" alt="">
      </div>
      <div class="inofor mt-2 mb-3"
     >
        <p>Hout Ky Sopanha</p>
        <i class="fa-solid fa-angle-up" style="color: lightgreen;"> <span class=" font-sans">Admin</span> </i>
      </div>
     </div>

      <!-- Sidebar Items -->
      <div class="sidebar-list overflow-y-auto force-overflow">
        <ul class="flex-1 mt-5 space-y-3">
        <li
          v-for="(item, index) in menuItems"
          :key="index"
          class="group"
        >
          <!-- Main Item -->
          <div
            class="flex items-center space-x-2 p-2 rounded-md hover:bg-gray-800 transition-all cursor-pointer"
            @click="toggleDropdown(index)"
          >
            <router-link :to="item.path" class="flex items-center">
              <i :class="item.icon" class="w-6 h-6 text-xl ml-3"></i>
            <span
              class="whitespace-nowrap transition-all duration-300 ml-5"
              :class="{ hidden: !isSidebarExpanded, block: isSidebarExpanded }"
            >
              {{ item.text }}
            </span>
            </router-link>
            <!-- Dropdown Indicator -->
            <i
              v-if="item.children"
              style="margin: 0;"
              class="fa-solid fa-chevron-down "
              :class="{ hidden: !isSidebarExpanded }"
            ></i>
          </div>

          <!-- Dropdown for Children -->
          <ul
            v-if="item.children && dropdownOpen === index"
            class="dropdown pl-8 space-y-1"
            v-show="isSidebarExpanded"
          >
            <li v-for="child in item.children" :key="child.text">
              <i :class="child.icon" class="w-6 h-6 text-sm ml-3 "></i>
              <router-link :to="child.path" class="text-sm hover:text-light-blue-500">
                {{ child.text }}
              </router-link>
            </li>
          </ul>
        </li>
      </ul>
      </div>
      <!-- Footer -->
      <div class="p-3 border-dashed border-t-2 border-light-blue-500">
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
      isSidebarExpanded: true, // Default expanded state
      dropdownOpen: null, // Track the open dropdown
      menuItems: [
  { icon: "fa-solid fa-tachometer-alt", text: "Dashboard", path: "/dashboard" },
  { icon: "fa-solid fa-hospital", text: "Hospital Department" },
  { icon: "fa-solid fa-user-md", text: "Doctor" },
  { icon: "fa-solid fa-user-injured", text: "Patient" },
  { icon: "fa-solid fa-calendar-check", text: "Doctor Schedule" },
  { icon: "fa-solid fa-calendar-day", text: "Patient Appointment" },
  { icon: "fa-solid fa-file-medical-alt", text: "Patient Case Study" },
  { icon: "fa-solid fa-prescription", text: "Prescription" },
  { icon: "fa-solid fa-shield-alt", text: "Insurance" },
  {
    icon: "fa-solid fa-flask",
    text: "Lab",
    path: "",
    children: [
      { icon: "fa-solid fa-vial", text: "Lab Report", path: "" },
      { icon: "fa-solid fa-file-medical", text: "Lab Report Template", path: "" }
    ]
  },
  {
    icon: "fa-solid fa-coins",
    text: "Financial Activities",
    path: "",
    children: [
      { icon: "fa-solid fa-user-tie", text: "Accountant Header", path: "" },
      { icon: "fa-solid fa-file-invoice", text: "Invoice", path: "" },
      { icon: "fa-solid fa-money-bill-wave", text: "Payment", path: "" },
      { icon: "fa-solid fa-chart-line", text: "Report", path: "" }
    ]
  },
  { icon: "fa-solid fa-code", text: "Front-ends" },
  { icon: "fa-solid fa-envelope", text: "Contact Us" },
  {
    icon: "fa-solid fa-envelope-open-text",
    text: "Email",
    path: "",
    children: [
      { icon: "fa-solid fa-envelope", text: "Email Templates", path: "" },
      { icon: "fa-solid fa-money-check-alt", text: "Payment", path: "" },
      { icon: "fa-solid fa-file-alt", text: "Report", path: "" }
    ]
  },
  {
    icon: "fa-solid fa-sms",
    text: "SMS",
    path: "",
    children: [
      { icon: "fa-solid fa-sms", text: "SMS Gateways", path: "" },
      { icon: "fa-solid fa-file-alt", text: "SMS Templates", path: "" },
      { icon: "fa-solid fa-bullhorn", text: "SMS Campaign", path: "" }
    ]
  },
  {
    icon: "fa-solid fa-cogs",
    text: "Settings",
    path: "",
    children: [
      { icon: "fa-solid fa-users-cog", text: "User  Management", path: "" },
      { icon: "fa-solid fa-tools", text: "Application Settings", path: "" },
      { icon: "fa-solid fa-envelope", text: "SMTP Settings", path: "" },
      { icon: "fa-solid fa-sliders-h", text: "General Settings", path: "" },
      { icon: "fa-solid fa-coins", text: "Currencies", path: "" },
      { icon: "fa-solid fa-percentage", text: "Tax Rates", path: "" }
    ]
  },
],
    }
  },
  methods: {
    toggleSidebar() {
      this.isSidebarExpanded = !this.isSidebarExpanded;
      this.dropdownOpen = null; // Close dropdowns when sidebar is toggled
    },
    toggleDropdown(index) {
      this.dropdownOpen = this.dropdownOpen === index ? null : index; // Toggle dropdown
    },
  },
};
</script>
<style>
.wrapper {
  /* display: flex; */
  height: 100vh;
  width: 100%;
  position: static;
}

.asidebar {
  width: auto;
  height: 100vh;
  background-color: lightslategrey;
}

/* Styling for expanded/collapsed sidebar */
.asidebar {
  transition: width 0.3s ease-in-out;
}
ul {
  list-style: none;
  padding: 0;
}
li {
  margin-bottom: 10px;
}
.dropdown {
  margin-left: 20px; /* Indent dropdown items */
  list-style: none;
  padding: 0;
}
.dropdown li {
  margin-bottom: 5px;
}
.asidebar {
  height: 100vh;
  transition: width 0.3s ease-in-out;
}

.dropdown {
  margin-left: 20px; /* Indent dropdown items */
  list-style: none;
  padding: 0;
}

.dropdown li {
  margin-bottom: 5px;
}

#style-3::-webkit-scrollbar-track
{
	-webkit-box-shadow: inset 0 0 6px rgba(0,0,0,0.3);
	background-color: #F5F5F5;
}

#style-3::-webkit-scrollbar
{
	width: 2px;
	background-color: #F5F5F5;
}

#style-3::-webkit-scrollbar-thumb
{
	background-color: #000000;
}
</style>

