<template>
  <div class="container mx-auto p-6">
    <h1 class="text-4xl font-bold text-indigo-600 mb-4">Criar Planejamento</h1>
    <form @submit.prevent="submitForm" class="space-y-4">
      <div>
        <label for="sinais_e_sintomas" class="block text-sm font-semibold text-gray-700"
          >Sinais e Sintomas</label
        >
        <input
          v-model="planejamento.sinais_e_sintomas"
          type="text"
          id="sinais_e_sintomas"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label
          for="resultados_esperados"
          class="block text-sm font-semibold text-gray-700"
          >Resultados Esperados</label
        >
        <input
          v-model="planejamento.resultados_esperados"
          type="text"
          id="resultados_esperados"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label for="intervencoes" class="block text-sm font-semibold text-gray-700"
          >Intervenções</label
        >
        <input
          v-model="planejamento.intervencoes"
          type="text"
          id="intervencoes"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label for="observacoes" class="block text-sm font-semibold text-gray-700"
          >Observações</label
        >
        <input
          v-model="planejamento.observacoes"
          type="text"
          id="observacoes"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <h2 class="text-lg font-semibold text-gray-700 mt-6">Implementação</h2>
      <div
        v-for="(value, key) in planejamento.implementacao"
        :key="key"
        class="flex items-center"
      >
        <input
          type="checkbox"
          v-model="planejamento.implementacao[key]"
          id="implementacao"
          class="mr-2"
        />
        <label :for="key" class="text-sm font-semibold text-gray-700 capitalize">{{
          key.replace(/_/g, " ")
        }}</label>
      </div>

      <button
        type="submit"
        class="mt-4 bg-indigo-600 text-white font-semibold py-2 px-4 rounded hover:bg-indigo-700 transition-colors"
      >
        Criar Planejamento
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

    const planejamento = ref({
      prontuario_id: 1, // ajuste conforme necessário
      sinais_e_sintomas: "",
      resultados_esperados: "",
      intervencoes: "",
      observacoes: "",
      implementacao: {
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
      },
    });

    const submitForm = async () => {
      console.log("Planejamento criado:", planejamento.value); // Verifica e exibe o planejamento a ser criado

      const storedPacientes = sessionStorage.getItem("pacientes");

      if (!storedPacientes) {
        console.error("Nenhum paciente encontrado na sessionStorage.");
        return;
      }

      // Converte a lista de pacientes do sessionStorage
      const pacientes = JSON.parse(storedPacientes);

      // Obtém o ID do prontuário da rota
      const prontuarioId = parseInt(route.params.id);
      const pacienteIndex = pacientes.findIndex((item) => item.id === prontuarioId);

      if (pacienteIndex === -1) {
        console.error("Paciente não encontrado.");
        return;
      }

      // Garante que o array de planejamentos exista
      if (!pacientes[pacienteIndex].planejamentos) {
        pacientes[pacienteIndex].planejamentos = []; // Inicializa como um array se não existir
      }

      // Adiciona o novo planejamento ao array de planejamentos do paciente
      pacientes[pacienteIndex].planejamentos.push(planejamento.value); // Adiciona o novo planejamento ao array existente

      console.log(pacientes[pacienteIndex]);

      // Armazena os pacientes atualizados de volta na sessionStorage
      sessionStorage.setItem("pacientes", JSON.stringify(pacientes)); // Salva a lista atualizada de pacientes

      // Redireciona para a página do paciente
      router.push(`/pacientes/${prontuarioId}`);
    };
    const goBack = () => {
      router.push(`/pacientes/${this.$route.params.id}/planejamentos`); // Redireciona de volta à lista de diagnósticos do paciente
    };

    return {
      planejamento,
      submitForm,
      goBack,
    };
  },
};
</script>
