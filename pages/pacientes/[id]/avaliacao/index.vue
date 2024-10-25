<template>
  <div class="container mx-auto p-6">
    <h1 class="text-4xl font-bold text-indigo-600 mb-4">Avaliação de Enfermagem</h1>

    <button
      @click="createAvaliacao"
      class="mb-4 bg-green-600 text-white font-semibold py-2 px-4 rounded hover:bg-green-700 transition-colors"
    >
      Nova Avaliação
    </button>

    <div v-if="paciente && paciente.avaliacao_enfermagem.length > 0" class="">
      <div
        v-for="(avaliacao, avIndex) in paciente.avaliacao_enfermagem"
        :key="avIndex"
        class="bg-white border border-gray-200 rounded-lg shadow-md p-4 mb-10"
      >
        <!-- Informações gerais da avaliação -->
        <h2 class="text-2xl font-semibold text-gray-800 mb-4">
          Avaliação #{{ avIndex + 1 }}
        </h2>
        <ul class="mb-4">
          <li>
            <strong>Processo Deliberado:</strong>
            {{ avaliacao.processo_deliberado ? "Sim" : "Não" }}
          </li>
          <li>
            <strong>Verificação de Respostas:</strong>
            {{ avaliacao.verificacao_respostas ? "Sim" : "Não" }}
          </li>
          <li>
            <strong>Determinação de Alcance de Resultados:</strong>
            {{ avaliacao.determinacao_alcance_resultados ? "Sim" : "Não" }}
          </li>
          <li>
            <strong>Verificação de Necessidade de Mudanças:</strong>
            {{ avaliacao.verificacao_necessidade_mudancas ? "Sim" : "Não" }}
          </li>
          <li>
            <strong>Investigação Abrangente:</strong>
            {{ avaliacao.investigacao_abranjente ? "Sim" : "Não" }}
          </li>
          <li>
            <strong>Decisão de Modificar, Manter ou Encerrar:</strong>
            {{ avaliacao.decisao_modificar_manter_encerrar ? "Sim" : "Não" }}
          </li>
          <li>
            <strong>Investigação Contínua:</strong>
            {{ avaliacao.investigacao_continua ? "Sim" : "Não" }}
          </li>
          <li>
            <strong>Revisão de Diagnósticos e Intervenções:</strong>
            {{ avaliacao.revisao_diagnosticos_intervencoes ? "Sim" : "Não" }}
          </li>
        </ul>

        <!-- Tabela de Anotações -->
        <div v-if="avaliacao.tabela_anotacao && avaliacao.tabela_anotacao.length > 0">
          <h3 class="text-xl font-semibold mb-2">Anotações</h3>
          <div
            v-for="(tabela, index) in avaliacao.tabela_anotacao"
            :key="index"
            class="mb-6 p-4 border border-gray-300 rounded-md"
          >
            <h4 class="text-xl font-semibold mb-2">Anotação #{{ index + 1 }}</h4>
            <p><strong>Necessidades Humanas Básicas:</strong> {{ tabela.nhb }}</p>
            <p><strong>Diagnóstico:</strong> {{ tabela.diagnostico }}</p>
            <p><strong>Resultado:</strong> {{ tabela.resultado }}</p>

            <!-- Exibe intervenções, se houver -->
            <div v-if="tabela.intervencoes && tabela.intervencoes.length > 0">
              <h5 class="text-lg font-semibold mt-2">Intervenções:</h5>
              <ul class="list-disc pl-6">
                <li v-for="(intervencao, i) in tabela.intervencoes" :key="i">
                  {{ intervencao }}
                </li>
              </ul>
            </div>
          </div>
        </div>
        <div v-else>
          <p class="text-gray-600">Nenhuma anotação encontrada.</p>
        </div>
      </div>
    </div>

    <div v-else>
      <p class="text-gray-600">
        Nenhum diagnóstico encontrado.
        <button @click="createAvaliacao" class="text-blue-400">Nova Avaliação</button>
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
    paciente.value = pacientes.find((item) => item.id === pacienteId);
    console.log(paciente.value); // Verifica os dados do paciente
  }
});

const createAvaliacao = () => {
  router.push(`/pacientes/${route.params.id}/nova-avaliacao`); // Redireciona para nova avaliação
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
