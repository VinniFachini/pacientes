<template>
  <div class="container mx-auto p-6">
    <h1 class="text-4xl font-bold text-indigo-600 mb-4">Criar Planejamento</h1>
    <form @submit.prevent="submitForm" class="space-y-4">
      <div>
        <label for="prontuario_id" class="block text-sm font-semibold text-gray-700">
          Número do Prontuário
        </label>
        <input
          v-model="planejamento.prontuario_id"
          type="text"
          id="prontuario_id"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label for="sinais_e_sintomas" class="block text-sm font-semibold text-gray-700">
          Sinais e Sintomas
        </label>
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
        >
          Resultados Esperados
        </label>
        <input
          v-model="planejamento.resultados_esperados"
          type="text"
          id="resultados_esperados"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label for="intervencoes" class="block text-sm font-semibold text-gray-700">
          Intervenções
        </label>
        <input
          v-model="planejamento.intervencoes"
          type="text"
          id="intervencoes"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label for="observacoes" class="block text-sm font-semibold text-gray-700">
          Observações
        </label>
        <input
          v-model="planejamento.observacoes"
          type="text"
          id="observacoes"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
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
      prontuario_id: "",
      sinais_e_sintomas: "",
      resultados_esperados: "",
      intervencoes: "",
      observacoes: "",
    });

    const submitForm = () => {
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

      // Cria o ID baseado no tamanho atual da array de planejamentos
      const novoId = pacientes[pacienteIndex].planejamentos
        ? pacientes[pacienteIndex].planejamentos.length + 1
        : 1;

      // Adiciona o ID ao planejamento
      const novoPlanejamento = {
        id: novoId,
        ...planejamento.value,
      };

      // Inicializa o array de planejamentos, se necessário, e adiciona o novo planejamento
      if (!pacientes[pacienteIndex].planejamentos) {
        pacientes[pacienteIndex].planejamentos = [];
      }
      pacientes[pacienteIndex].planejamentos.push(novoPlanejamento);

      // Atualiza a sessionStorage com o novo planejamento
      sessionStorage.setItem("pacientes", JSON.stringify(pacientes));

      // Redireciona para a página do paciente
      router.push(`/pacientes/${pacienteId}/planejamentos`);
    };

    const goBack = () => {
      router.push(`/pacientes/${route.params.id}/planejamentos`);
    };

    return {
      planejamento,
      submitForm,
      goBack,
    };
  },
};
</script>
