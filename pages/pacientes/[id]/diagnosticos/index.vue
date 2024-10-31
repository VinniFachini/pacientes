<template>
  <div class="container mx-auto p-6">
    <h1 class="text-4xl font-bold text-indigo-600">Diagnósticos</h1>

    <button
      @click="createDiagnostico"
      class="my-4 bg-green-600 text-white font-semibold py-2 px-4 rounded hover:bg-green-700 transition-colors"
    >
      Novo Diagnóstico
    </button>

    <div
      v-if="paciente && paciente.diagnosticos && paciente.diagnosticos.length"
      class="py-4"
    >
      <div
        v-for="diagnostico in paciente.diagnosticos"
        :key="diagnostico.id"
        class="mb-4 p-4 border border-gray-300 rounded-md"
      >
        <h2 class="text-2xl font-semibold text-gray-800">
          Diagnóstico #{{ diagnostico.id }}
        </h2>
        <p class="text-gray-600">
          <strong>Prontuário:</strong> {{ diagnostico.prontuario }}
        </p>
        <p class="text-gray-600">
          <strong>Problemas de Saúde:</strong> {{ diagnostico.problemas_saude }}
        </p>
        <p class="text-gray-600"><strong>Riscos:</strong> {{ diagnostico.riscos }}</p>
        <p class="text-gray-600">
          <strong>Sinais ou Sintomas:</strong> {{ diagnostico.sinais_ou_sintomas }}
        </p>
        <p class="text-gray-600">
          <strong>Aprendizado:</strong> {{ diagnostico.aprendizado }}
        </p>
        <p class="text-gray-600"><strong>Recursos:</strong> {{ diagnostico.recursos }}</p>
        <p class="text-gray-600">
          <strong>Estado de Saúde:</strong> {{ diagnostico.estado_de_saude }}
        </p>

        <button
          class="mt-4 bg-indigo-600 text-white font-semibold py-2 px-4 rounded hover:bg-indigo-700 transition-colors"
          @click="goToDiagnostico(diagnostico.id)"
        >
          Ver Diagnóstico
        </button>
      </div>
    </div>
    <div v-else>
      <p class="text-gray-600">
        Nenhum diagnóstico encontrado.
        <button @click="createDiagnostico" class="text-blue-400">Novo Diagnóstico</button>
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
const paciente = ref(null); // Armazena os dados do paciente

onMounted(() => {
  // Recupera os dados do SessionStorage
  const storedPacientes = sessionStorage.getItem("pacientes");
  const pacienteId = parseInt(route.params.id); // Obtém o ID do paciente da rota

  if (storedPacientes) {
    const pacientes = JSON.parse(storedPacientes);
    console.log();
    paciente.value = pacientes.find((item) => item.id === pacienteId);
  }
});

const goToDiagnostico = (id) => {
  router.push(`/pacientes/${route.params.id}/diagnosticos/${id}`);
};

const createDiagnostico = (id) => {
  router.push(`/pacientes/${route.params.id}/novo-diagnostico`);
};

// Função para voltar à página do paciente
const goBack = () => {
  const id = Number(route.params.id); // Obtém o ID da rota
  router.push(`/pacientes/${id}`); // Redireciona de volta à lista de pacientes
};
</script>

<style scoped>
/* Estilos adicionais se necessário */
</style>
