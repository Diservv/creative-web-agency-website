<template>
  <main>
    <!-- Hero Section -->
    <section id="home" class="min-h-screen flex items-center relative overflow-hidden pt-20">
      <div class="container mx-auto px-4 grid grid-cols-1 md:grid-cols-2 gap-12 items-center mt-8 pt-8 md:mt-0 md:pt-4">
        <!-- Left Content -->
        <div class="text-left">
          <h1 class="text-6xl md:text-7xl font-bold mb-8 bg-clip-text text-transparent bg-gradient-to-r from-blue-600 via-purple-600 to-blue-600" style="line-height: 1.2;">
            Criamos <span class="relative inline-block">
              <span class="bg-clip-text text-transparent bg-gradient-to-r from-blue-600 to-purple-600">
                experiências
              </span>
              <span 
                class="absolute left-0 -bottom-3 w-full h-3 bg-[#f9ff00] rounded-md"
              ></span>
            </span> digitais
          </h1>
          <p class="text-2xl text-gray-600 mb-10 font-light leading-relaxed max-w-2xl">
            Transforme sua marca com soluções web de ponta que cativam e convertem seus clientes.
          </p>
          <div class="flex gap-4 flex-wrap">
            <!-- "Get Started" Button -->
            <Button 
              @click="scrollToSection('services')" 
              label="Começar Agora" 
              icon="pi pi-arrow-right" 
              class="p-button-rounded p-button-lg custom-get-started shadow-lg hover:shadow-xl"
            />
            <!-- "Our Work" Button -->
            <Button 
              @click="scrollToSection('portfolio')" 
              label="Ver Projetos" 
              icon="pi pi-images" 
              class="p-button-rounded p-button-lg custom-our-work shadow-lg hover:shadow-xl"
            />
          </div>
        </div>
        <!-- Right Illustration -->
        <div class="relative">
          <img 
            src="/hero-img.svg"
            alt="Creative workspace"
            class="rounded-2xl transform hover:scale-105 transition-transform duration-300"
          />
          <!-- Decorative Elements -->
          <div class="absolute -top-8 -right-8 w-32 h-32 bg-blue-500/10 rounded-full blur-2xl"></div>
          <div class="absolute -bottom-8 -left-8 w-32 h-32 bg-purple-500/10 rounded-full blur-2xl"></div>
        </div>
      </div>
    </section>

    <!-- About Section -->
    <section id="about" class="py-32 bg-gradient-to-b from-white via-blue-50/30 to-white">
      <div class="container mx-auto px-4">
        <div class="grid grid-cols-1 md:grid-cols-2 gap-20 items-center">
          <div>
            <h2 class="text-5xl font-bold mb-8 bg-clip-text text-transparent bg-gradient-to-r from-blue-600 to-purple-600">Quem Somos</h2>
            <p class="text-lg text-gray-600 mb-6 leading-relaxed">
              Fundada em 2024, estamos na vanguarda da inovação digital, ajudando empresas a transformar sua presença online e alcançar um crescimento notável.
            </p>
            <p class="text-lg text-gray-600 mb-8 leading-relaxed">
              Nossa equipe combina criatividade com expertise técnica para entregar soluções que não apenas parecem excelentes, mas também impulsionam resultados reais para o negócio.
            </p>
            <div class="grid grid-cols-2 gap-8">
              <div v-for="stat in aboutStats" :key="stat.label" class="text-center p-4 bg-white rounded-xl shadow-md hover:shadow-lg transition-all">
                <div class="text-3xl font-bold text-blue-600 mb-2">{{ stat.value }}</div>
                <div class="text-sm text-gray-600 font-medium">{{ stat.label }}</div>
              </div>
            </div>
          </div>
          <div class="relative group">
            <div class="absolute inset-0 bg-gradient-to-r from-blue-600 to-purple-600 rounded-2xl blur-2xl opacity-20 group-hover:opacity-30 transition-opacity"></div>
            <img
              src="https://images.unsplash.com/photo-1522071820081-009f0129c71c?auto=format&fit=crop&q=80&w=800"
              alt="Team meeting"
              class="rounded-2xl shadow-2xl relative transform group-hover:scale-105 transition-transform duration-300"
            />
          </div>
        </div>
      </div>
    </section>

    <!-- Services Section -->
    <section id="services" class="py-32 bg-gradient-to-b from-gray-50 to-white">
      <div class="container mx-auto px-4">
        <div class="text-center mb-20">
          <h2 class="text-5xl font-bold mb-6 bg-clip-text text-transparent bg-gradient-to-r from-blue-600 to-purple-600">Nossos Serviços</h2>
          <p class="text-xl text-gray-600 max-w-3xl mx-auto">Soluções digitais abrangentes, personalizadas para as necessidades do seu negócio.</p>
        </div>
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
          <div v-for="service in services" :key="service.title" class="transform transition-all duration-300 hover:scale-105">
            <ServiceCard v-bind="service" />
          </div>
        </div>
      </div>
    </section>

    <!-- Portfolio Section -->
    <section id="portfolio" class="py-32 bg-gradient-to-b from-white to-blue-50/20">
      <div class="container mx-auto px-4">
        <div class="text-center mb-20">
          <h2 class="text-5xl font-bold mb-6 bg-clip-text text-transparent bg-gradient-to-r from-blue-600 to-purple-600">Nosso Portfólio</h2>
          <p class="text-xl text-gray-600 max-w-3xl mx-auto">Descubra nossos projetos mais recentes e histórias de sucesso.</p>
        </div>
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8 mb-12">
          <div v-for="project in displayedProjects" :key="project.title" class="transform transition-all duration-300 hover:scale-105">
            <ProjectCard v-bind="project" />
          </div>
        </div>

        <!-- Show More / Show Less Button -->
        <div class="text-center mb-32 mt-8" v-if="projects.length > 4">
          <Button 
            @click="toggleShowMore" 
            :label="showMoreProjects ? 'Ver Menos Projetos' : 'Ver Mais Projetos (4 de ' + projects.length + ')'"
            :icon="showMoreProjects ? 'pi pi-chevron-up' : 'pi pi-chevron-down'"
            class="p-button-outlined p-button-lg font-semibold shadow-lg hover:shadow-xl transform transition-all duration-200 hover:-translate-y-1" 
            severity="info"
          />
        </div>

        <!-- Stats Section -->
        <div class="grid grid-cols-2 md:grid-cols-4 gap-8">
          <div 
            v-for="stat in portfolioStats" 
            :key="stat.label"
            class="text-center p-6 bg-white rounded-xl shadow-lg hover:shadow-xl transition-shadow"
          >
            <div class="text-3xl font-bold text-blue-600 mb-2">{{ stat.value }}</div>
            <div class="text-gray-600">{{ stat.label }}</div>
          </div>
        </div>
      </div>
    </section>

    <!-- Contact Section -->
    <section id="contact" class="py-32 bg-gradient-to-b from-gray-50 via-white to-blue-50/20">
      <div class="container mx-auto px-4">
        <div class="text-center mb-20">
          <h2 class="text-5xl font-bold mb-6 bg-clip-text text-transparent bg-gradient-to-r from-blue-600 to-purple-600">Entre em Contato Conosco</h2>
          <p class="text-xl text-gray-600 max-w-3xl mx-auto">Adoramos ouvir de você. Entre em contato com nossa equipe hoje e vamos criar algo incrível juntos.</p>
        </div>
        <div class="grid grid-cols-1 lg:grid-cols-2 gap-16 max-w-6xl mx-auto">
          <!-- Contact Form -->
          <div class="bg-white p-10 rounded-2xl shadow-xl hover:shadow-2xl transition-shadow">
            <div class="flex items-center gap-3 mb-8">
              <div class="w-12 h-12 bg-gradient-to-br from-blue-600 to-purple-600 rounded-lg flex items-center justify-center">
                <i class="pi pi-send text-white text-xl"></i>
              </div>
              <h3 class="text-2xl font-bold">Envie-nos uma Mensagem</h3>
            </div>
            <form @submit.prevent="handleContactSubmit" class="space-y-6">
              <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                <div>
                  <label class="block text-sm font-semibold text-gray-700 mb-2">Primeiro Nome</label>
                  <input
                    v-model="contactForm.firstName"
                    type="text"
                    placeholder="Ex: João"
                    class="w-full px-4 py-3 border-2 border-gray-200 rounded-lg focus:border-blue-500 focus:ring-2 focus:ring-blue-200 transition-all outline-none"
                    required
                  />
                </div>
                <div>
                  <label class="block text-sm font-semibold text-gray-700 mb-2">Último Nome</label>
                  <input
                    v-model="contactForm.lastName"
                    type="text"
                    placeholder="Ex: Silva"
                    class="w-full px-4 py-3 border-2 border-gray-200 rounded-lg focus:border-blue-500 focus:ring-2 focus:ring-blue-200 transition-all outline-none"
                    required
                  />
                </div>
              </div>
              <div>
                <label class="block text-sm font-semibold text-gray-700 mb-2">Email</label>
                <input
                  v-model="contactForm.email"
                  type="email"
                  placeholder="seu@email.com"
                  class="w-full px-4 py-3 border-2 border-gray-200 rounded-lg focus:border-blue-500 focus:ring-2 focus:ring-blue-200 transition-all outline-none"
                  required
                />
              </div>
              <div>
                <label class="block text-sm font-semibold text-gray-700 mb-2">Mensagem</label>
                <textarea
                  v-model="contactForm.message"
                  rows="5"
                  placeholder="Descreva seu projeto ou dúvida..."
                  class="w-full px-4 py-3 border-2 border-gray-200 rounded-lg focus:border-blue-500 focus:ring-2 focus:ring-blue-200 transition-all outline-none resize-none"
                  required
                ></textarea>
              </div>
              <Button 
                type="submit" 
                :label="isSubmitting ? 'Enviando...' : 'Enviar Mensagem'" 
                icon="pi pi-send" 
                :loading="isSubmitting"
                :disabled="isSubmitting"
                class="w-full p-button-lg font-semibold shadow-lg hover:shadow-xl transform transition-all duration-200 hover:-translate-y-1"
                style="background: linear-gradient(135deg, #5A58E9 0%, #4745C9 100%)"
              />
            </form>
          </div>

          <!-- Contact Information -->
          <div>
            <div class="flex items-center gap-3 mb-12">
              <div class="w-12 h-12 bg-gradient-to-br from-blue-600 to-purple-600 rounded-lg flex items-center justify-center">
                <i class="pi pi-phone text-white text-xl"></i>
              </div>
              <h3 class="text-2xl font-bold">Informações de Contato</h3>
            </div>
            <div class="space-y-6 mb-12">
              <div v-for="item in contactInfo" :key="item.title" class="flex items-start gap-4 p-4 rounded-xl hover:bg-blue-50 transition-colors">
                <div class="p-3 bg-blue-100 rounded-lg flex-shrink-0">
                  <i :class="item.icon + ' text-xl text-blue-600'"></i>
                </div>
                <div>
                  <h4 class="font-bold text-lg text-gray-800 mb-1">{{ item.title }}</h4>
                  <p class="text-gray-600">{{ item.content }}</p>
                </div>
              </div>
            </div>

            <!-- Social Media Links -->
            <div class="p-6 bg-gradient-to-br from-blue-50 to-purple-50 rounded-xl">
              <h3 class="font-bold text-lg mb-4 text-gray-800">Siga-nos nas Redes Sociais</h3>
              <div class="flex gap-4">
                <a v-for="social in socialLinks" 
                   :key="social.icon"
                   href="#"
                   class="w-12 h-12 bg-white rounded-full hover:bg-blue-600 hover:text-white text-gray-600 flex items-center justify-center transition-all duration-300 shadow-md hover:shadow-lg transform hover:scale-110">
                  <i :class="social.icon + ' text-lg'"></i>
                </a>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
  </main>
</template>

<script setup>
import { reactive, ref, computed } from 'vue';
import ServiceCard from '@/components/services/ServiceCard.vue';
import ProjectCard from '@/components/portfolio/ProjectCard.vue';
import { services } from '@/data/services';
import { projects } from '@/data/projects';

const contactForm = reactive({
  firstName: '',
  lastName: '',
  email: '',
  message: ''
});

const showMoreProjects = ref(false);
const isSubmitting = ref(false);

const displayedProjects = computed(() => {
  return showMoreProjects.value ? projects : projects.slice(0, 4);
});

const toggleShowMore = () => {
  showMoreProjects.value = !showMoreProjects.value;
};

const scrollToSection = (id) => {
  const element = document.getElementById(id);
  if (element) {
    element.scrollIntoView({ behavior: 'smooth' });
  }
};

const handleContactSubmit = async () => {
  isSubmitting.value = true;
  try {
    console.log('Form submitted:', contactForm);
    // Simular delay de envio
    await new Promise(resolve => setTimeout(resolve, 1500));
    alert('✓ Mensagem enviada com sucesso!\nEntraremos em contato em breve.');
    contactForm.firstName = '';
    contactForm.lastName = '';
    contactForm.email = '';
    contactForm.message = '';
  } finally {
    isSubmitting.value = false;
  }
};

const portfolioStats = [
  { value: '10+', label: 'Projetos Entregues' },
  { value: '98%', label: 'Satisfação do Cliente' },
  { value: '2+', label: 'Prêmios da Indústria' },
  { value: '24/7', label: 'Suporte Disponível' }
];

const aboutStats = [
  { value: '10+', label: 'Projetos Concluídos' },
  { value: '20+', label: 'Clientes Felizes' },
  { value: '5+', label: 'Membros da Equipe' },
  { value: '2+', label: 'Anos de Experiência' }
];

const contactInfo = [
  {
    icon: 'pi pi-map-marker',
    title: 'Visite-nos',
    content: '123 Creative Street, Design District, CA 90210'
  },
  {
    icon: 'pi pi-envelope',
    title: 'Email',
    content: 'hello@creative-agency.com'
  },
  {
    icon: 'pi pi-phone',
    title: 'Ligue para nós',
    content: '+1 (555) 123-4567'
  },
  {
    icon: 'pi pi-clock',
    title: 'Horário de Funcionamento',
    content: 'Segunda - Sexta: 9:00 AM - 6:00 PM'
  }
];

const socialLinks = [
  { icon: 'pi pi-facebook' },
  { icon: 'pi pi-twitter' },
  { icon: 'pi pi-instagram' },
  { icon: 'pi pi-linkedin' }
];
</script>

<style scoped>
/* Custom "Get Started" Button */
.custom-get-started {
  background-color: #EBED9E !important;
  color: #000 !important;
  border: none !important;
  font-weight: 600;
  transition: all 0.3s ease;
}

.custom-get-started:hover {
  background-color: #f2ff00 !important;
  transform: translateY(-2px);
}

/* Custom "Our Work" Button */
.custom-our-work {
  background: linear-gradient(135deg, #5A58E9 0%, #4745C9 100%) !important;
  color: #fff !important;
  border: none !important;
  font-weight: 600;
  transition: all 0.3s ease;
}

.custom-our-work:hover {
  transform: translateY(-2px);
}

/* Smooth section transitions */
section {
  transition: background-color 0.3s ease;
}
</style>
