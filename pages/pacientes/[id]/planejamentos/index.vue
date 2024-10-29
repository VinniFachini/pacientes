<template>
  <div class="container mx-auto p-6">
    <h1 class="text-4xl font-bold text-indigo-600 mb-4">Planejamentos</h1>

    <button
      @click="createPlanejamento"
      class="mb-4 bg-green-600 text-white font-semibold py-2 px-4 rounded hover:bg-green-700 transition-colors"
    >
      Novo Planejamento
    </button>

    <div v-if="planejamentos.length" class="bg-white py-4">
      <div
        v-for="planejamento in planejamentos"
        :key="planejamento.id"
        class="mb-4 p-4 border border-gray-300 rounded-md"
      >
        <h2 class="text-2xl font-semibold text-gray-800">
          Planejamento #{{ planejamento.id }}
        </h2>
        <p class="text-gray-600">
          <strong>Prontuário ID:</strong> {{ planejamento.prontuario_id }}
        </p>
        <p class="text-gray-600">
          <strong>Sinais e Sintomas:</strong>
          {{ planejamento.sinais_e_sintomas || "N/A" }}
        </p>
        <p class="text-gray-600">
          <strong>Resultados Esperados:</strong>
          {{ planejamento.resultados_esperados || "N/A" }}
        </p>
        <p class="text-gray-600">
          <strong>Intervenções:</strong> {{ planejamento.intervencoes || "N/A" }}
        </p>
        <p class="text-gray-600">
          <strong>Observações:</strong> {{ planejamento.observacoes || "N/A" }}
        </p>
      </div>
    </div>
    <div v-else>
      <p class="text-gray-600">
        Nenhum planejamento encontrado.
        <button @click="createPlanejamento" class="text-blue-400">
          Novo Planejamento
        </button>
      </p>
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
const router = useRouter();
const planejamentos = ref([]); // Armazena os planejamentos do paciente

onMounted(() => {
  // Recupera os dados do SessionStorage
  const storedPacientes = sessionStorage.getItem("pacientes");
  const pacienteId = parseInt(route.params.id); // Obtém o ID do paciente da rota

  if (storedPacientes) {
    const pacientes = JSON.parse(storedPacientes);
    planejamentos.value = pacientes.find((item) => item.id === pacienteId).planejamentos;
  }
});

// Função para voltar à página anterior
const goBack = () => {
  router.push(`/pacientes/${route.params.id}`); // Redireciona de volta à lista de diagnósticos do paciente
};
const createPlanejamento = () => {
  router.push(`/pacientes/${route.params.id}/novo-planejamento`); // Redireciona de volta à lista de diagnósticos do paciente
};
</script>

<style scoped>
/* Estilos adicionais se necessário */
</style>
