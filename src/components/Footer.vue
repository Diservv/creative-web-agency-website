<template>
  <footer class="bg-gray-900 text-white py-12">
    <div class="container mx-auto px-4">
      <div class="grid grid-cols-1 md:grid-cols-4 gap-8">
        <div>
          <div class="flex items-center gap-2 mb-4">
            <h3 class="font-bold text-xl" style="color: #EBED9E;">Creative</h3>
          </div>
          <p class="text-gray-400">
            Crafting digital experiences that inspire and innovate.
          </p>
        </div>
        <div>
          <h3 class="font-bold mb-4"  style="color: #EBED9E;">Services</h3>
          <ul class="space-y-2 text-gray-400">
            <li>
              <button @click="scrollToSection('services')" class="hover:text-blue-400 transition-colors cursor-pointer">Web Design</button>
            </li>
            <li>
              <button @click="scrollToSection('services')" class="hover:text-blue-400 transition-colors cursor-pointer">Development</button>
            </li>
            <li>
              <button @click="scrollToSection('services')" class="hover:text-blue-400 transition-colors cursor-pointer">Branding</button>
            </li>
            <li>
              <button @click="scrollToSection('services')" class="hover:text-blue-400 transition-colors cursor-pointer">Digital Marketing</button>
            </li>
          </ul>
        </div>
        <div>
          <h3 class="font-bold mb-4"  style="color: #EBED9E;">Company</h3>
          <ul class="space-y-2 text-gray-400">
            <li>
              <button @click="scrollToSection('about')" class="hover:text-blue-400 transition-colors cursor-pointer">About Us</button>
            </li>
            <li>
              <button @click="scrollToSection('portfolio')" class="hover:text-blue-400 transition-colors cursor-pointer">Portfolio</button>
            </li>
            <li>
              <button @click="scrollToSection('portfolio')" class="hover:text-blue-400 transition-colors cursor-pointer">Work</button>
            </li>
            <li>
              <button @click="scrollToSection('contact')" class="hover:text-blue-400 transition-colors cursor-pointer">Contact</button>
            </li>
          </ul>
        </div>
        <div>
          <h3 class="font-bold mb-4"  style="color: #EBED9E;">Connect</h3>
          <div class="flex gap-4">
            <i class="pi pi-facebook text-xl cursor-pointer hover:text-blue-400"></i>
            <i class="pi pi-twitter text-xl cursor-pointer hover:text-blue-400"></i>
            <i class="pi pi-instagram text-xl cursor-pointer hover:text-blue-400"></i>
            <i class="pi pi-linkedin text-xl cursor-pointer hover:text-blue-400"></i>
          </div>
        </div>
      </div>
      <div class="border-t border-gray-800 mt-8 pt-8 text-center text-gray-400">
        <p>&copy; {{ new Date().getFullYear() }} Creative Agency. All rights reserved.</p>
      </div>
    </div>
  </footer>
</template>

<script setup>
const scrollToSection = (id) => {
  const element = document.getElementById(id);
  if (element) {
    element.scrollIntoView({ behavior: 'smooth' });
  }
};
</script>
