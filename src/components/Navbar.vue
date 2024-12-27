<script setup lang="ts">
import { ref, watch } from "vue";
import { useThemeStore } from "../store/theme";

const themeStore = useThemeStore();

const themes = ref<string[]>(["Light", "Dark"]);
const selectedTheme = ref<string>(themeStore.theme.charAt(0).toUpperCase() + themeStore.theme.slice(1));

const isDropdownOpen = ref<boolean>(false);

const toggleDropdown = () => {
  isDropdownOpen.value = !isDropdownOpen.value;
};

const toggleTheme = (theme: string) => {
  themeStore.theme = theme.toLowerCase();
  themeStore.applyTheme();
  isDropdownOpen.value = false;
};

watch(
  () => themeStore.theme,
  (newTheme) => {
    selectedTheme.value = newTheme.charAt(0).toUpperCase() + newTheme.slice(1);
  }
);
</script>
<template>
  <div :data-theme="themeStore.theme">
    <div class="w-[95%] mx-auto px-4 sm:px-6 lg:px-8 mt-2 mb-6 flex items-center justify-between">
      <img src="../assets/images/Navbar/Logo.png" alt="Logo" class="hidden lg:block w-68 h-16">
      <div class="flex space-x-8 items-center">
        <router-link :to="{ name: 'home' }" class="group">
          <div class="relative group">
            <i
              class="bi bi-house-door-fill text-2xl text-gray-800 md:block lg:hidden group-hover:text-purple-700"
              :class="{ 'text-white': themeStore.theme === 'dark' }"
            ></i>
            <span
              class="absolute top-full left-1/2 transform -translate-x-1/2 text-sm font-semibold md:block lg:hidden text-gray-800 opacity-0 transition-all duration-300 group-hover:bottom-[0] group-hover:opacity-100"
              :class="{ 'text-white': themeStore.theme === 'dark' }"
            >
              Home
            </span>
          </div>
          <span
            class="hidden lg:inline-block font-semibold text-xl text-gray-800 group relative hover:text-purple-700"
            :class="{ 'text-white hover:text-purple-400': themeStore.theme === 'dark' }"
          >
            Home
            <span
              class="absolute left-0 bottom-[-2px] w-0 h-1 rounded-xl bg-purple-700 transition-all duration-300 ease-in-out group-hover:w-full"
              :class="{ 'bg-purple-400': themeStore.theme === 'dark' }"
            ></span>
          </span>
        </router-link>

        <router-link :to="{ name: 'about' }" class="group">
          <div class="relative group">
            <i
              class="bi bi-info-circle-fill text-2xl text-gray-800 md:block lg:hidden group-hover:text-purple-700"
              :class="{ 'text-white': themeStore.theme === 'dark' }"
            ></i>
            <span
              class="absolute top-full left-1/2 transform -translate-x-1/2 text-sm font-semibold md:block lg:hidden text-gray-800 opacity-0 transition-all duration-300 group-hover:bottom-[0] group-hover:opacity-100"
              :class="{ 'text-white': themeStore.theme === 'dark' }"
            >
              About
            </span>
          </div>
          <span
            class="hidden lg:inline-block font-semibold text-xl text-gray-800 group relative hover:text-purple-700"
            :class="{ 'text-white hover:text-purple-400': themeStore.theme === 'dark' }"
          >
            About
            <span
              class="absolute left-0 bottom-[-2px] w-0 h-1 rounded-xl bg-purple-700 transition-all duration-300 ease-in-out group-hover:w-full"
              :class="{ 'bg-purple-400': themeStore.theme === 'dark' }"
            ></span>
          </span>
        </router-link>

        <router-link :to="{ name: 'projects' }" class="group">
          <div class="relative group">
            <i
              class="bi bi-info-circle-fill text-2xl text-gray-800 md:block lg:hidden group-hover:text-purple-700"
              :class="{ 'text-white': themeStore.theme === 'dark' }"
            ></i>
            <span
              class="absolute top-full left-1/2 transform -translate-x-1/2 text-sm font-semibold md:block lg:hidden text-gray-800 opacity-0 transition-all duration-300 group-hover:bottom-[0] group-hover:opacity-100"
              :class="{ 'text-white': themeStore.theme === 'dark' }"
            >
              Projects
            </span>
          </div>
          <span
            class="hidden lg:inline-block font-semibold text-xl text-gray-800 group relative hover:text-purple-700"
            :class="{ 'text-white hover:text-purple-400': themeStore.theme === 'dark' }"
          >
            Projects
            <span
              class="absolute left-0 bottom-[-2px] w-0 h-1 rounded-xl bg-purple-700 transition-all duration-300 ease-in-out group-hover:w-full"
              :class="{ 'bg-purple-400': themeStore.theme === 'dark' }"
            ></span>
          </span>
        </router-link>

        <router-link :to="{ name: 'contact' }" class="group">
          <div class="relative group">
            <i
              class="bi bi-info-circle-fill text-2xl text-gray-800 md:block lg:hidden group-hover:text-purple-700"
              :class="{ 'text-white': themeStore.theme === 'dark' }"
            ></i>
            <span
              class="absolute top-full left-1/2 transform -translate-x-1/2 text-sm font-semibold md:block lg:hidden text-gray-800 opacity-0 transition-all duration-300 group-hover:bottom-[0] group-hover:opacity-100"
              :class="{ 'text-white': themeStore.theme === 'dark' }"
            >
              Contact
            </span>
          </div>
          <span
            class="hidden lg:inline-block font-semibold text-xl text-gray-800 group relative hover:text-purple-700"
            :class="{ 'text-white hover:text-purple-400': themeStore.theme === 'dark' }"
          >
            Contact
            <span
              class="absolute left-0 bottom-[-2px] w-0 h-1 rounded-xl bg-purple-700 transition-all duration-300 ease-in-out group-hover:w-full"
              :class="{ 'bg-purple-400': themeStore.theme === 'dark' }"
            ></span>
          </span>
        </router-link>

        <!-- Dropdown for theme selection -->
        <div
          @click="toggleDropdown"
          class="relative p-2 rounded-lg shadow-sm flex items-center gap-2 cursor-pointer"
          :class="{ 'bg-white shadow-lg shadow-black ': themeStore.theme === 'light', 'bg-[#323131]': themeStore.theme === 'dark' }"
        >
          <p
            class="font-semibold text-xl"
            :class="{ 'text-black': themeStore.theme === 'light', 'text-white': themeStore.theme === 'dark' }"
          >
            Theme
          </p>
          <div
            v-if="isDropdownOpen"
            class="absolute top-full left-0 border rounded-md shadow-md mt-1 w-full z-10"
            :class="{
              'bg-white border-gray-300 shadow-gray-700': themeStore.theme === 'light',
              'bg-gray-900 border-purple-900': themeStore.theme === 'dark'
            }"
          >
            <p
              v-for="theme in themes"
              :key="theme"
              @click.stop="toggleTheme(theme)"
              class="py-1 px-2 font-semibold cursor-pointer border-b"
              :class="{
                'text-black hover:bg-gray-100 border-gray-300': themeStore.theme === 'light',
                'text-white hover:bg-gray-800 border-purple-900': themeStore.theme === 'dark'
              }"
            >
              {{ theme }}
            </p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
a:hover {
  transition: all 0.3s ease;
}
</style>