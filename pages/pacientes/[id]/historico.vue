<template>
  <div class="container mx-auto p-6">
    <h3 class="text-3xl font-semibold text-gray-800 mt-4">Histórico</h3>

    <!-- Verifique se 'paciente' está disponível antes de acessar suas propriedades -->
    <div
      class="gap-4 grid grid-cols-1 md:grid-cols-2"
      v-if="paciente && paciente.historico"
    >
      <!-- Identificação -->
      <div class="mt-4">
        <h4 class="font-semibold text-2xl mb-2">Identificação</h4>
        <p class="text-gray-600"><strong>Nome:</strong> {{ paciente.nome }}</p>
        <p class="text-gray-600">
          <strong>Idade:</strong> {{ paciente.historico.identificacao.idade }} anos
        </p>
        <p class="text-gray-600">
          <strong>Leito:</strong> {{ paciente.historico.identificacao.leito }}
        </p>
        <p class="text-gray-600">
          <strong>Estado Civil:</strong>
          {{ paciente.historico.identificacao.estado_civil }}
        </p>
        <p class="text-gray-600">
          <strong>Filhos:</strong>
          {{ paciente.historico.identificacao.filhos }}
        </p>
        <p class="text-gray-600">
          <strong>Gênero:</strong> {{ paciente.historico.identificacao.genero }}
        </p>
        <p class="text-gray-600">
          <strong>Escolaridade:</strong>
          {{ paciente.historico.identificacao.escolaridade }}
        </p>
        <p class="text-gray-600">
          <strong>Étnia:</strong> {{ paciente.historico.identificacao.etnia }}
        </p>
        <p class="text-gray-600">
          <strong>Ocupação:</strong> {{ paciente.historico.identificacao.ocupacao }}
        </p>
        <p class="text-gray-600">
          <strong>Naturalidade:</strong>
          {{ paciente.historico.identificacao.naturalidade }}
        </p>
        <p class="text-gray-600">
          <strong>Procedência:</strong> {{ paciente.historico.identificacao.procedencia }}
        </p>
        <p class="text-gray-600">
          <strong>Religião:</strong> {{ paciente.historico.identificacao.religiao }}
        </p>
        <p class="text-gray-600">
          <strong>Cuidador:</strong> {{ paciente.historico.identificacao.cuidador }}
        </p>
        <p class="text-gray-600">
          <strong>Grupo Sanguíneo:</strong>
          {{ paciente.historico.identificacao.grupo_sanguineo }}
        </p>
        <p class="text-gray-600">
          <strong>Fator Rh:</strong> {{ paciente.historico.identificacao.fator_rh }}
        </p>
      </div>

      <!-- Informações sobre Doença e Tratamento -->
      <div class="mt-4">
        <h4 class="font-semibold text-2xl mb-2">Informações sobre Doença e Tratamento</h4>
        <p class="text-gray-600">
          <strong>Motivo da Internação:</strong>
          {{
            paciente.historico.informacoes_doenca_tratamento.motivo_internacao || "N/A"
          }}
        </p>
        <p class="text-gray-600">
          <strong>Diagnóstico Médico:</strong>
          {{
            paciente.historico.informacoes_doenca_tratamento.diagnostico_medico || "N/A"
          }}
        </p>
        <p class="text-gray-600">
          <strong>Doenças Crônicas:</strong>
          {{ paciente.historico.informacoes_doenca_tratamento.doencas_cronicas || "N/A" }}
        </p>
        <p class="text-gray-600">
          <strong>Fatores de Risco:</strong>
          {{ paciente.historico.informacoes_doenca_tratamento.fatores_risco || "N/A" }}
        </p>
        <p class="text-gray-600">
          <strong>Alergias a Medicamentos:</strong>
          {{
            paciente.historico.informacoes_doenca_tratamento.alergias_medicamentos
              ? "Sim"
              : "Não"
          }}
        </p>
        <p class="text-gray-600">
          <strong>Especificar:</strong>
          {{ paciente.historico.informacoes_doenca_tratamento.especificar || "N/A" }}
        </p>
        <p class="text-gray-600">
          <strong>Tratamentos Anteriores:</strong>
          {{
            paciente.historico.informacoes_doenca_tratamento.tratamentos_anteriores ||
            "N/A"
          }}
        </p>
        <p class="text-gray-600">
          <strong>Cirurgias:</strong>
          {{ paciente.historico.informacoes_doenca_tratamento.cirurgias ? "Sim" : "Não" }}
        </p>
        <p class="text-gray-600">
          <strong>Outros Tratamentos:</strong>
          {{
            paciente.historico.informacoes_doenca_tratamento.outros_tratamentos || "N/A"
          }}
        </p>
      </div>

      <!-- Socioeconômicos e Culturais -->
      <div class="mt-4">
        <h4 class="font-semibold text-2xl mb-2">Socioeconômicos e Culturais</h4>
        <p class="text-gray-600">
          <strong>Moradia:</strong>
          {{ paciente.historico.socio_economicos_culturais.moradia }}
        </p>
        <p class="text-gray-600">
          <strong>Animais Domésticos:</strong>
          {{ paciente.historico.socio_economicos_culturais.animais_domesticos || "N/A" }}
        </p>
      </div>

      <!-- Higiene -->
      <div class="mt-4">
        <h4 class="font-semibold text-2xl mb-2">Higiene</h4>
        <p class="text-gray-600">
          <strong>Hábito de Tomar Banho:</strong>
          {{ paciente.historico.higiene.habito_tomar_banho }}
        </p>
        <p class="text-gray-600">
          <strong>Atividade Física no Trabalho:</strong>
          {{ paciente.historico.higiene.atividade_fisica_trabalho }}
        </p>
        <p class="text-gray-600">
          <strong>Fumo:</strong> {{ paciente.historico.higiene.fumo || "N/A" }}
        </p>
        <p class="text-gray-600">
          <strong>Álcool:</strong> {{ paciente.historico.higiene.alcool || "N/A" }}
        </p>
        <p class="text-gray-600">
          <strong>Sonos e Repouso:</strong>
          {{ paciente.historico.higiene.sono_repouso || "N/A" }}
        </p>
        <p class="text-gray-600">
          <strong>Exercícios Físicos:</strong>
          {{ paciente.historico.higiene.exercicios_fisicos || "N/A" }}
        </p>
        <p class="text-gray-600">
          <strong>Eliminação Urinária:</strong>
          {{ paciente.historico.higiene.eliminacao_urinaria || "N/A" }}
        </p>
        <p class="text-gray-600">
          <strong>Eliminações Intestinais:</strong>
          {{ paciente.historico.higiene.eliminacoes_intestinais || "N/A" }}
        </p>
      </div>
    </div>
    <div v-else>
      <p class="text-gray-500">
        Paciente não possui histórico...
        <button @click="createHistorico" class="text-blue-400">Criar Histórico</button>
      </p>
    </div>

    <!-- Botão para voltar -->
    <div class="mt-6">
      <button
        @click="goBack"
        class="px-4 py-2 bg-blue-600 text-white rounded hover:bg-blue-700"
      >
        Voltar ao Paciente
      </button>
    </div>
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
  }
  console.log(paciente.value);
});

const createHistorico = () => {
  const id = Number(route.params.id); // Obtém o ID da rota
  router.push(`/pacientes/${id}/criar-historico`);
};

// Função para voltar à página do paciente
const goBack = () => {
  const id = Number(route.params.id); // Obtém o ID da rota
  router.push(`/pacientes/${id}`); // Redireciona de volta à lista de pacientes
};
</script>
