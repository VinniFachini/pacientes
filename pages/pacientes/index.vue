<template>
  <div class="flex flex-col items-start justify-between min-h-screen">
    <Header />

    <div
      class="main-content flex-grow flex flex-col items-center justify-start p-6 max-w-4xl"
    >
      <h1 class="text-4xl font-bold text-indigo-600 mb-4">Pacientes</h1>
      <button
        @click="newPaciente"
        class="my-4 bg-indigo-600 text-white font-semibold py-2 px-4 rounded hover:bg-indigo-700 transition-colors"
      >
        Novo Paciente
      </button>
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4">
        <div
          v-for="paciente in pacientes"
          :key="paciente.id"
          class="bg-white border border-gray-200 rounded-lg shadow-md p-4"
        >
          <h2 class="text-xl font-semibold text-gray-800">{{ paciente.nome }}</h2>
          <p class="text-gray-600"><strong>CPF:</strong> {{ paciente.cpf }}</p>
          <button
            @click="viewDetails(paciente.id)"
            class="mt-2 w-full bg-indigo-600 text-white font-semibold py-2 rounded hover:bg-indigo-700 transition-colors"
          >
            Ver Detalhes
          </button>
        </div>
      </div>
    </div>
    <Footer />
  </div>
</template>

<script setup>
import { ref, onMounted } from "vue";
import { useRouter } from "vue-router";

const router = useRouter();
const pacientes = ref([]); // Armazena a lista de pacientes

onMounted(async () => {
  // Recupera os dados do SessionStorage
  const storedPacientes = sessionStorage.getItem("pacientes");
  if (storedPacientes) {
    pacientes.value = JSON.parse(storedPacientes);
    console.log(pacientes.value);
  }
});

const viewDetails = (id) => {
  const paciente = pacientes.value.find((p) => p.id === id); // Busca o paciente pelo ID
  if (paciente) {
    router.push(`/pacientes/${id}`); // Redireciona para a página de detalhes do paciente
  } else {
    console.error("Paciente não encontrado");
  }
};
const newPaciente = () => {
  router.push(`/pacientes/novo-paciente`); // Redireciona para a página de detalhes do paciente
};
</script>

<style scoped>
/* Estilos adicionais se necessário */
</style>
