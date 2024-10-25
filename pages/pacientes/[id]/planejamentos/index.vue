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

        <h4 class="font-bold">Implementação</h4>
        <ul class="pl-2">
          <li>
            <label>
              <strong class="mr-2">Lavar Mãos:</strong>
              <input
                type="checkbox"
                disabled
                :checked="planejamento.implementacao.lavar_maos"
              />
            </label>
          </li>
          <li>
            <label class="flex items-center justify-start">
              <strong class="mr-2">Uso de Luva:</strong>
              <input
                type="checkbox"
                disabled
                :checked="planejamento.implementacao.uso_luva"
              />
            </label>
          </li>
          <li>
            <label class="flex items-center justify-start">
              <strong class="mr-2">Orientar Cliente:</strong>
              <input
                type="checkbox"
                disabled
                :checked="planejamento.implementacao.orientar_cliente"
              />
            </label>
          </li>
          <li>
            <label class="flex items-center justify-start">
              <strong class="mr-2">Sinais Vitais:</strong>
              <input
                type="checkbox"
                disabled
                :checked="planejamento.implementacao.sinais_vitais"
              />
            </label>
          </li>
          <li>
            <label class="flex items-center justify-start">
              <strong class="mr-2">Administrar Medicação:</strong>
              <input
                type="checkbox"
                disabled
                :checked="planejamento.implementacao.administrar_medicacao"
              />
            </label>
          </li>
          <li>
            <label class="flex items-center justify-start">
              <strong class="mr-2">Frequência Cardíaca:</strong>
              <input
                type="checkbox"
                disabled
                :checked="planejamento.implementacao.frequencia_cardiaca"
              />
            </label>
          </li>
          <li>
            <label class="flex items-center justify-start">
              <strong class="mr-2">Banho e Hidratação:</strong>
              <input
                type="checkbox"
                disabled
                :checked="planejamento.implementacao.banho_hidratacao"
              />
            </label>
          </li>
          <li>
            <label class="flex items-center justify-start">
              <strong class="mr-2">Higiene Íntima:</strong>
              <input
                type="checkbox"
                disabled
                :checked="planejamento.implementacao.higiene_intima"
              />
            </label>
          </li>
          <li>
            <label class="flex items-center justify-start">
              <strong class="mr-2">Higiene Oral:</strong>
              <input
                type="checkbox"
                disabled
                :checked="planejamento.implementacao.higiene_oral"
              />
            </label>
          </li>
          <li>
            <label class="flex items-center justify-start">
              <strong class="mr-2">Dispneia e Saturação:</strong>
              <input
                type="checkbox"
                disabled
                :checked="planejamento.implementacao.dispneia_saturacao"
              />
            </label>
          </li>
          <li>
            <label class="flex items-center justify-start">
              <strong class="mr-2">Auxílio à Deambulação:</strong>
              <input
                type="checkbox"
                disabled
                :checked="planejamento.implementacao.auxilio_deambulacao"
              />
            </label>
          </li>
          <li>
            <label class="flex items-center justify-start">
              <strong class="mr-2">Estimulo à Deambulação:</strong>
              <input
                type="checkbox"
                disabled
                :checked="planejamento.implementacao.estimulo_deambulacao"
              />
            </label>
          </li>
          <li>
            <label class="flex items-center justify-start">
              <strong class="mr-2">Medicação Oral:</strong>
              <input
                type="checkbox"
                disabled
                :checked="planejamento.implementacao.medicacao_oral"
              />
            </label>
          </li>
          <li>
            <label class="flex items-center justify-start">
              <strong class="mr-2">Ingesta Hídrica:</strong>
              <input
                type="checkbox"
                disabled
                :checked="planejamento.implementacao.ingesta_hidrica"
              />
            </label>
          </li>
          <li>
            <label class="flex items-center justify-start">
              <strong class="mr-2">Distensão Abdominal:</strong>
              <input
                type="checkbox"
                disabled
                :checked="planejamento.implementacao.distensao_abdominal"
              />
            </label>
          </li>
          <li>
            <label class="flex items-center justify-start">
              <strong class="mr-2">Elevar Decúbito:</strong>
              <input
                type="checkbox"
                disabled
                :checked="planejamento.implementacao.elevar_decubito"
              />
            </label>
          </li>
          <li>
            <label class="flex items-center justify-start">
              <strong class="mr-2">Jogos Cognitivos:</strong>
              <input
                type="checkbox"
                disabled
                :checked="planejamento.implementacao.jogos_cognitivos"
              />
            </label>
          </li>
          <li>
            <label class="flex items-center justify-start">
              <strong class="mr-2">Elevar MMII:</strong>
              <input
                type="checkbox"
                disabled
                :checked="planejamento.implementacao.elevar_mmii"
              />
            </label>
          </li>
          <li>
            <label class="flex items-center justify-start">
              <strong class="mr-2">Perfusão das Extremidades:</strong>
              <input
                type="checkbox"
                disabled
                :checked="planejamento.implementacao.perfusao_extremidades"
              />
            </label>
          </li>
          <li>
            <label class="flex items-center justify-start">
              <strong class="mr-2">Anotar Diurese:</strong>
              <input
                type="checkbox"
                disabled
                :checked="planejamento.implementacao.anotar_diurese"
              />
            </label>
          </li>
          <li>
            <label class="flex items-center justify-start">
              <strong class="mr-2">Anotar Evacuação:</strong>
              <input
                type="checkbox"
                disabled
                :checked="planejamento.implementacao.anotar_evacuacao"
              />
            </label>
          </li>
          <li>
            <label class="flex items-center justify-start">
              <strong class="mr-2">Integridade da Pele:</strong>
              <input
                type="checkbox"
                disabled
                :checked="planejamento.implementacao.integridade_pele"
              />
            </label>
          </li>
          <li>
            <label class="flex items-center justify-start">
              <strong class="mr-2">Alterações Neurológicas:</strong>
              <input
                type="checkbox"
                disabled
                :checked="planejamento.implementacao.alteracoes_neurologicas"
              />
            </label>
          </li>
          <li>
            <label class="flex items-center justify-start">
              <strong class="mr-2">Mudança de Decúbito:</strong>
              <input
                type="checkbox"
                disabled
                :checked="planejamento.implementacao.mudanca_decubito"
              />
            </label>
          </li>
          <li>
            <label class="flex items-center justify-start">
              <strong class="mr-2">Uso de Sapatos Confortáveis:</strong>
              <input
                type="checkbox"
                disabled
                :checked="planejamento.implementacao.sapatos_confortaveis"
              />
            </label>
          </li>
          <li>
            <label class="flex items-center justify-start">
              <strong class="mr-2">Ouvir o Cliente:</strong>
              <input
                type="checkbox"
                disabled
                :checked="planejamento.implementacao.ouvir_cliente"
              />
            </label>
          </li>
          <li>
            <label class="flex items-center justify-start">
              <strong class="mr-2">Manter Ambiente Limpo:</strong>
              <input
                type="checkbox"
                disabled
                :checked="planejamento.implementacao.manter_ambiente_limpo"
              />
            </label>
          </li>
        </ul>
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
    console.log();
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
