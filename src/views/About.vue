<template>
  <main>
    <PageHeader
      title="Sobre nós"
      description="Somos uma equipe de criadores e inovadores apaixonados"
    />
    
    <section class="py-16 bg-white">
      <div class="container mx-auto px-4">
        <div class="grid grid-cols-1 md:grid-cols-2 gap-16 items-center">
          <div>
            <h2 class="text-3xl font-bold mb-6">Nossa História</h2>
            <p class="text-gray-600 mb-4">
              Fundada em 2024, estamos na vanguarda da inovação digital, ajudando empresas a transformar sua presença online e alcançar um crescimento notável.
            </p>
            <p class="text-gray-600 mb-6">
              Nossa equipe combina criatividade com expertise técnica para entregar soluções que não apenas parecem excelentes, mas também impulsionam resultados reais para o negócio.
            </p>
            <div class="grid grid-cols-2 gap-8">
              <div v-for="stat in stats" :key="stat.label" class="text-center">
                <div class="text-4xl font-bold text-blue-600 mb-2">{{ stat.value }}</div>
                <div class="text-gray-600">{{ stat.label }}</div>
              </div>
            </div>
          </div>
          <div class="relative">
            <img
              src="https://images.unsplash.com/photo-1522071820081-009f0129c71c?auto=format&fit=crop&q=80&w=800"
              alt="Team meeting"
              class="rounded-lg shadow-xl"
            />
          </div>
        </div>
      </div>
    </section>
  </main>
</template>

<script setup>
import PageHeader from '@/components/shared/PageHeader.vue';

const stats = [
  { value: '10+', label: 'Projects Completed' },
  { value: '20+', label: 'Happy Clients' },
  { value: '5+', label: 'Team Members' },
  { value: '2+', label: 'Years Experience' }
];
</script>