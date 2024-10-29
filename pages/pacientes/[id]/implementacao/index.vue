<template>
  <div class="container mx-auto p-6">
    <h1 class="text-4xl font-bold text-indigo-600 mb-4">Implementações</h1>

    <button
      @click="createPlanejamento"
      class="mb-4 bg-green-600 text-white font-semibold py-2 px-4 rounded hover:bg-green-700 transition-colors"
    >
      Nova Implementação
    </button>

    <div v-if="planejamentos && planejamentos.length" class="bg-white py-4">
      <div
        v-for="(implementacao, index) in planejamentos"
        :key="index"
        class="mb-4 p-4 border border-gray-300 rounded-md"
      >
        <!-- Número do Prontuário -->
        <h4 class="font-bold text-lg mb-2">
          Prontuário: {{ implementacao.numeroProntuario }}
        </h4>

        <!-- Lista de Implementações -->
        <ul class="pl-2">
          <li v-for="(value, key) in implementacao" :key="key">
            <!-- Exibe apenas se não for o número do prontuário -->
            <div v-if="key !== 'numeroProntuario'">
              <label class="flex items-center justify-start">
                <strong class="mr-2 capitalize">{{ formatLabel(key) }}:</strong>
                <input type="checkbox" disabled :checked="value" />
              </label>
            </div>
          </li>
        </ul>
      </div>
    </div>

    <div v-else>
      <p class="text-gray-600">
        Nenhuma implementação encontrada.
        <button @click="createPlanejamento" class="text-blue-400">
          Nova Implementação
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
const planejamentos = ref([]); // Armazena as implementações do paciente

onMounted(() => {
  const storedPacientes = sessionStorage.getItem("pacientes");
  const pacienteId = parseInt(route.params.id);

  if (storedPacientes) {
    const pacientes = JSON.parse(storedPacientes);
    planejamentos.value = pacientes.find((item) => item.id === pacienteId).implementacao;
    console.log(planejamentos.value);
  }
});

// Função para redirecionar à criação de nova implementação
const createPlanejamento = () => {
  router.push(`/pacientes/${route.params.id}/nova-implementacao`);
};

// Função para voltar à página anterior
const goBack = () => {
  router.push(`/pacientes/${route.params.id}`);
};

// Formatação do rótulo de cada implementação
const formatLabel = (label) => {
  return label.replace(/_/g, " ");
};
</script>

<style scoped>
/* Estilos adicionais se necessário */
</style>
