<template>
  <div class="container mx-auto p-6">
    <h1 class="text-4xl font-bold text-indigo-600 mb-4">Detalhes do Paciente</h1>
    <div v-if="paciente" class="">
      <h2 class="text-2xl font-semibold text-gray-800">{{ paciente.nome }}</h2>
      <p class="text-gray-600"><strong>CPF:</strong> {{ paciente.cpf }}</p>
      <p class="text-gray-600"><strong>Nascimento:</strong> {{ paciente.nascimento }}</p>

      <h3 class="text-xl font-semibold text-gray-800 mt-4">Prontuários</h3>
      <button
        @click="newProntuario"
        class="my-4 bg-green-600 text-white font-semibold py-2 px-4 rounded hover:bg-green-700 transition-colors"
      >
        Novo Prontuário
      </button>
      <div
        v-for="prontuario in paciente.prontuarios"
        :key="prontuario.id"
        class="mb-4 p-4 border border-gray-300 rounded-md"
      >
        <h4 class="font-bold">Prontuário #{{ prontuario.id }}</h4>
        <p class="text-gray-600"><strong>PA:</strong> {{ prontuario.pa }}</p>
        <p class="text-gray-600"><strong>FR:</strong> {{ prontuario.fr }}</p>
        <p class="text-gray-600"><strong>FC:</strong> {{ prontuario.fc }}</p>
        <p class="text-gray-600">
          <strong>Temperatura:</strong> {{ prontuario.temperatura }} °C
        </p>
        <p class="text-gray-600"><strong>Saturação:</strong> {{ prontuario.spo2 }}%</p>
        <p class="text-gray-600"><strong>Altura:</strong> {{ prontuario.altura }} cm</p>
        <p class="text-gray-600"><strong>Peso:</strong> {{ prontuario.peso }} kg</p>
      </div>

      <div class="flex items-center justify-start gap-2">
        <button
          @click="viewHistoricos"
          class="mt-4 bg-blue-600 text-white font-semibold py-2 px-4 rounded hover:bg-blue-700 transition-colors"
        >
          Histórico de Enfermagem
        </button>
        <button
          @click="viewDiagnosticos"
          class="mt-4 bg-blue-600 text-white font-semibold py-2 px-4 rounded hover:bg-blue-700 transition-colors"
        >
          Diagnósticos
        </button>
        <button
          @click="viewPlanejamentos"
          class="mt-4 bg-blue-600 text-white font-semibold py-2 px-4 rounded hover:bg-blue-700 transition-colors"
        >
          Planejamentos
        </button>
        <button
          @click="viewAvaliacao"
          class="mt-4 bg-blue-600 text-white font-semibold py-2 px-4 rounded hover:bg-blue-700 transition-colors"
        >
          Avaliação
        </button>
      </div>
    </div>
    <div v-else>
      <p class="text-gray-600">Carregando detalhes do paciente...</p>
    </div>
    <button
      @click="goBack"
      class="mt-4 bg-indigo-600 text-white font-semibold py-2 px-4 rounded hover:bg-indigo-700 transition-colors"
    >
      Voltar
    </button>
  </div>
</template>

<script setup>
import { ref, onMounted } from "vue";
import { useRoute, useRouter } from "vue-router";

const route = useRoute();
const router = useRouter(); // Inicializa o router
const paciente = ref(null); // Armazena os dados do paciente
const pacientes = ref(null); // Armazena os dados do paciente

onMounted(async () => {
  // Recupera os dados do SessionStorage
  const storedPacientes = sessionStorage.getItem("pacientes");
  const pacienteId = parseInt(route.params.id); // Obtém o ID do paciente da rota

  if (storedPacientes) {
    const parsedPacientes = JSON.parse(storedPacientes);

    // Verifica se parsedPacientes é um array
    if (Array.isArray(parsedPacientes)) {
      pacientes.value = parsedPacientes;
      console.log(pacientes.value);
      // Busca o paciente pelo ID
      paciente.value = pacientes.value.find((item) => item.id === pacienteId);
    } else {
      console.error("Os dados armazenados não são um array.");
    }
  } else {
    console.warn("Nenhum paciente encontrado no sessionStorage.");
  }

  console.log(paciente.value);
});
// Função para ver os históricos do paciente
const viewHistoricos = () => {
  const id = Number(route.params.id);
  router.push(`/pacientes/${id}/historico`); // Redireciona para a rota de históricos
};
const newProntuario = () => {
  const id = Number(route.params.id);
  router.push(`/pacientes/${id}/novo-prontuario`); // Redireciona para a rota de históricos
};
const viewDiagnosticos = () => {
  const id = Number(route.params.id);
  router.push(`/pacientes/${id}/diagnosticos`); // Redireciona para a rota de históricos
};
const viewPlanejamentos = () => {
  const id = Number(route.params.id);
  router.push(`/pacientes/${id}/planejamentos`); // Redireciona para a rota de históricos
};
const viewAvaliacao = () => {
  const id = Number(route.params.id);
  router.push(`/pacientes/${id}/avaliacao`); // Redireciona para a rota de históricos
};

// Função para voltar à página anterior
const goBack = () => {
  router.push("/pacientes"); // Redireciona de volta à lista de pacientes
};
</script>

<style scoped>
/* Estilos adicionais se necessário */
</style>
