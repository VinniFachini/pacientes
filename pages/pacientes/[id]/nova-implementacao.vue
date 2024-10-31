<template>
  <div class="container mx-auto p-6">
    <h1 class="text-4xl font-bold text-indigo-600 mb-4">Criar Implementação</h1>
    <form @submit.prevent="submitForm" class="space-y-4">
      <h2 class="text-lg font-semibold text-gray-700 mt-6">Número do Prontuário</h2>
      <div>
        <input
          type="text"
          v-model="numeroProntuario"
          placeholder="Digite o número do prontuário"
          class="w-full p-2 border border-gray-300 rounded"
        />
      </div>

      <h2 class="text-lg font-semibold text-gray-700 mt-6">Implementação</h2>
      <div v-for="(value, key) in implementacao" :key="key" class="flex items-center">
        <input type="checkbox" v-model="implementacao[key]" :id="key" class="mr-2" />
        <label :for="key" class="text-sm font-semibold text-gray-700 capitalize">{{
          key.replace(/_/g, " ")
        }}</label>
      </div>

      <button
        type="submit"
        class="mt-4 bg-indigo-600 text-white font-semibold py-2 px-4 rounded hover:bg-indigo-700 transition-colors"
      >
        Criar Implementação
      </button>
    </form>
    <button
      @click="goBack()"
      class="mt-4 bg-green-600 text-white font-semibold py-2 px-4 rounded hover:bg-green-700 transition-colors"
    >
      Voltar
    </button>
  </div>
</template>

<script>
import { ref } from "vue";
import { useRoute, useRouter } from "vue-router";

export default {
  setup() {
    const route = useRoute();
    const router = useRouter();

    const numeroProntuario = ref(""); // Campo para o número do prontuário
    const implementacao = ref({
      lavar_maos: false,
      uso_luva: false,
      orientar_cliente: false,
      sinais_vitais: false,
      administrar_medicacao: false,
      frequencia_cardiaca: false,
      banho_hidratacao: false,
      higiene_intima: false,
      higiene_oral: false,
      dispneia_saturacao: false,
      auxilio_deambulacao: false,
      estimulo_deambulacao: false,
      medicacao_oral: false,
      ingesta_hidrica: false,
      distensao_abdominal: false,
      elevar_decubito: false,
      jogos_cognitivos: false,
      elevar_mmii: false,
      perfusao_extremidades: false,
      anotar_diurese: false,
      anotar_evacuacao: false,
      integridade_pele: false,
      alteracoes_neurologicas: false,
      mudanca_decubito: false,
      sapatos_confortaveis: false,
      ouvir_cliente: false,
      manter_ambiente_limpo: false,
    });

    const submitForm = async () => {
      if (!numeroProntuario.value) {
        console.error("Número do prontuário não preenchido.");
        return;
      }

      console.log("Implementação criada:", implementacao.value);

      const storedPacientes = sessionStorage.getItem("pacientes");

      if (!storedPacientes) {
        console.error("Nenhum paciente encontrado na sessionStorage.");
        return;
      }

      const pacientes = JSON.parse(storedPacientes);

      const pacienteId = parseInt(route.params.id);
      const pacienteIndex = pacientes.findIndex((item) => item.id === pacienteId);

      if (pacienteIndex === -1) {
        console.error("Paciente não encontrado.");
        return;
      }

      if (!pacientes[pacienteIndex].implementacao) {
        pacientes[pacienteIndex].implementacao = [];
      }

      // Cria uma nova implementação com o número do prontuário incluído
      const novaImplementacao = {
        ...implementacao.value,
        numeroProntuario: numeroProntuario.value, // Adiciona o número do prontuário
      };

      // Adiciona o novo planejamento ao array de implementações do paciente
      pacientes[pacienteIndex].implementacao.push(novaImplementacao);

      console.log(pacientes[pacienteIndex]);

      // Salva a lista atualizada de pacientes
      sessionStorage.setItem("pacientes", JSON.stringify(pacientes));

      // Redireciona para a página do paciente
      router.push(`/pacientes/${pacienteId}`);
    };

    const goBack = () => {
      router.push(`/pacientes/${route.params.id}/implementacao`);
    };

    return {
      numeroProntuario,
      implementacao,
      submitForm,
      goBack,
    };
  },
};
</script>
