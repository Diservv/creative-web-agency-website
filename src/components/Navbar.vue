<template>
  <Menubar :model="items" class="border-none shadow-md backdrop-blur-md fixed w-full z-50 bg-white/95">
    <template #start>
      <div class="flex items-center gap-3 pl-4">
        <div class="w-10 h-10 bg-gradient-to-br from-blue-600 to-purple-600 rounded-lg flex items-center justify-center">
          <i class="pi pi-bolt text-white font-bold text-lg"></i>
        </div>
        <span class="font-bold text-lg bg-clip-text text-transparent bg-gradient-to-r from-blue-600 to-purple-600">Creative</span>
      </div>
    </template>
    <template #end>
      <Button @click="scrollToSection('contact')" label="Contact Us" icon="pi pi-send" class="p-button-rounded p-button-sm bg-[#4745C9] text-white hover:bg-[#3633A2] transition-all mr-4" />
    </template>
  </Menubar>
</template>

<script setup>
const scrollToSection = (id) => {
  const element = document.getElementById(id);
  if (element) {
    element.scrollIntoView({ behavior: 'smooth' });
  }
};

const items = [
  {
    label: 'Home',
    icon: 'pi pi-home',
    command: () => window.scrollTo({ top: 0, behavior: 'smooth' }),
    class: 'text-gray-700 font-medium hover:text-blue-600'
  },
  {
    label: 'About',
    icon: 'pi pi-users',
    command: () => scrollToSection('about'),
    class: 'text-gray-700 font-medium hover:text-blue-600'
  },
  {
    label: 'Services',
    icon: 'pi pi-star',
    command: () => scrollToSection('services'),
    class: 'text-gray-700 font-medium hover:text-blue-600'
  },
  {
    label: 'Portfolio',
    icon: 'pi pi-images',
    command: () => scrollToSection('portfolio'),
    class: 'text-gray-700 font-medium hover:text-blue-600'
  }
];
</script>
