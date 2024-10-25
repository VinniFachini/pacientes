<template>
    <div class="container mx-auto p-6">
        <h1 class="text-4xl font-bold text-indigo-600 mb-4">Detalhes do Diagnóstico</h1>

        <div v-if="diagnostico" class="bg-white border border-gray-200 rounded-lg shadow-md p-4">
            <h2 class="text-2xl font-semibold text-gray-800">Diagnóstico #{{ diagnostico.id }}</h2>
            <p class="text-gray-600"><strong>Prontuário:</strong> {{ diagnostico.prontuario }}</p>
            <p class="text-gray-600"><strong>Problemas de Saúde:</strong> {{ diagnostico.problemas_saude }}</p>
            <p class="text-gray-600"><strong>Riscos:</strong> {{ diagnostico.riscos }}</p>
            <p class="text-gray-600"><strong>Sinais ou Sintomas:</strong> {{ diagnostico.sinais_ou_sintomas }}</p>
            <p class="text-gray-600"><strong>Aprendizado:</strong> {{ diagnostico.aprendizado }}</p>
            <p class="text-gray-600"><strong>Recursos:</strong> {{ diagnostico.recursos }}</p>
            <p class="text-gray-600"><strong>Estado de Saúde:</strong> {{ diagnostico.estado_de_saude }}</p>

        </div>
        <div v-else>
            <p class="text-gray-600">Diagnóstico não encontrado.</p>
        </div>

        <button @click="goBack" class="mt-4 bg-indigo-600 text-white font-semibold py-2 px-4 rounded hover:bg-indigo-700 transition-colors">
            Voltar
        </button>
    </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import { useRoute, useRouter } from 'vue-router';

const route = useRoute();
const router = useRouter();
const diagnostico = ref(null); // Armazena os dados do diagnóstico

onMounted(() => {
  // Recupera os dados do SessionStorage
  const storedPacientes = sessionStorage.getItem('pacientes')
  const pacienteId = parseInt(route.params.id) // Obtém o ID do paciente da rota
  const diagnosticoID = parseInt(route.params.diagnosticoId)
  
  if (storedPacientes) {
    const pacientes = JSON.parse(storedPacientes)
    diagnostico.value = pacientes.find(item => item.id === pacienteId).diagnosticos.find(item => item.id === diagnosticoID)
    console.log(diagnostico.value)
  }
})

// Função para voltar à página anterior
const goBack = () => {
    router.push(`/pacientes/${route.params.id}/diagnosticos`); // Redireciona de volta à lista de diagnósticos do paciente
};
</script>

<style scoped>
/* Estilos adicionais se necessário */
</style>
