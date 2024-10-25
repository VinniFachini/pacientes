<template>
  <div class="container mx-auto p-6">
    <h1 class="text-4xl font-bold text-indigo-600 mb-4">Criar Avaliação de Enfermagem</h1>
    <form @submit.prevent="submitForm" class="space-y-4">
      <h2 class="text-lg font-semibold text-gray-700">Avaliação de Enfermagem</h2>
      <div class="space-y-2">
        <div class="flex items-center">
          <input
            type="checkbox"
            v-model="avaliacao_enfermagem.processo_deliberado"
            id="processo_deliberado"
            class="mr-2"
          />
          <label for="processo_deliberado" class="text-sm font-semibold text-gray-700"
            >Processo Deliberado</label
          >
        </div>
        <div class="flex items-center">
          <input
            type="checkbox"
            v-model="avaliacao_enfermagem.verificacao_respostas"
            id="verificacao_respostas"
            class="mr-2"
          />
          <label for="verificacao_respostas" class="text-sm font-semibold text-gray-700"
            >Verificação de Respostas</label
          >
        </div>
        <div class="flex items-center">
          <input
            type="checkbox"
            v-model="avaliacao_enfermagem.determinacao_alcance_resultados"
            id="determinacao_alcance_resultados"
            class="mr-2"
          />
          <label
            for="determinacao_alcance_resultados"
            class="text-sm font-semibold text-gray-700"
            >Determinação de Alcance de Resultados</label
          >
        </div>
        <div class="flex items-center">
          <input
            type="checkbox"
            v-model="avaliacao_enfermagem.verificacao_necessidade_mudancas"
            id="verificacao_necessidade_mudancas"
            class="mr-2"
          />
          <label
            for="verificacao_necessidade_mudancas"
            class="text-sm font-semibold text-gray-700"
            >Verificação de Necessidade de Mudanças</label
          >
        </div>
        <div class="flex items-center">
          <input
            type="checkbox"
            v-model="avaliacao_enfermagem.investigacao_abranjente"
            id="investigacao_abranjente"
            class="mr-2"
          />
          <label for="investigacao_abranjente" class="text-sm font-semibold text-gray-700"
            >Investigação Abrangente</label
          >
        </div>
        <div class="flex items-center">
          <input
            type="checkbox"
            v-model="avaliacao_enfermagem.decisao_modificar_manter_encerrar"
            id="decisao_modificar_manter_encerrar"
            class="mr-2"
          />
          <label
            for="decisao_modificar_manter_encerrar"
            class="text-sm font-semibold text-gray-700"
            >Decisão de Modificar/Manter/Encerrar</label
          >
        </div>
        <div class="flex items-center">
          <input
            type="checkbox"
            v-model="avaliacao_enfermagem.investigacao_continua"
            id="investigacao_continua"
            class="mr-2"
          />
          <label for="investigacao_continua" class="text-sm font-semibold text-gray-700"
            >Investigação Contínua</label
          >
        </div>
        <div class="flex items-center">
          <input
            type="checkbox"
            v-model="avaliacao_enfermagem.revisao_diagnosticos_intervencoes"
            id="revisao_diagnosticos_intervencoes"
            class="mr-2"
          />
          <label
            for="revisao_diagnosticos_intervencoes"
            class="text-sm font-semibold text-gray-700"
            >Revisão de Diagnósticos/Intervenções</label
          >
        </div>
      </div>

      <h2 class="text-lg font-semibold text-gray-700 mt-6">Tabela de Anotação</h2>
      <div
        v-for="(item, index) in avaliacao_enfermagem.tabela_anotacao"
        :key="index"
        class="border p-4 rounded-md"
      >
        <div>
          <label class="block text-sm font-semibold text-gray-700">NHB</label>
          <input
            v-model="item.nhb"
            type="text"
            class="mt-1 block w-full border border-gray-300 rounded-md p-2"
          />
        </div>
        <div>
          <label class="block text-sm font-semibold text-gray-700">Diagnóstico</label>
          <input
            v-model="item.diagnostico"
            type="text"
            class="mt-1 block w-full border border-gray-300 rounded-md p-2"
          />
        </div>
        <div>
          <label class="block text-sm font-semibold text-gray-700">Resultado</label>
          <input
            v-model="item.resultado"
            type="text"
            class="mt-1 block w-full border border-gray-300 rounded-md p-2"
          />
        </div>
        <div>
          <label class="block text-sm font-semibold text-gray-700">Intervenções</label>
          <div
            v-for="(intervencao, i) in item.intervencoes"
            :key="i"
            class="flex items-center"
          >
            <input
              v-model="item.intervencoes[i]"
              type="text"
              class="mt-1 block w-full border border-gray-300 rounded-md p-2 mb-2"
            />
          </div>
          <button
            type="button"
            @click="addIntervencao(index)"
            class="text-indigo-600 hover:underline"
          >
            Adicionar Intervenção
          </button>
        </div>
      </div>

      <button
        type="button"
        @click="this.$router.push(`/pacientes/${this.$route.params.id}/avaliacao`)"
        class="mt-4 mr-2 bg-green-600 text-white font-semibold py-2 px-4 rounded hover:bg-green-700 transition-colors"
      >
        Voltar
      </button>
      <button
        type="button"
        @click="addAnotacao"
        class="mt-4 mr-2 bg-indigo-600 text-white font-semibold py-2 px-4 rounded hover:bg-indigo-700 transition-colors"
      >
        Adicionar Anotação
      </button>

      <button
        type="submit"
        class="mt-4 bg-indigo-600 text-white font-semibold py-2 px-4 rounded hover:bg-indigo-700 transition-colors"
      >
        Criar Avaliação
      </button>
    </form>
  </div>
</template>

<script>
import { ref } from "vue";
import { useRoute, useRouter } from "vue-router";

export default {
  setup() {
    const route = useRoute();
    const router = useRouter();

    const avaliacao_enfermagem = ref({
      processo_deliberado: false,
      verificacao_respostas: false,
      determinacao_alcance_resultados: false,
      verificacao_necessidade_mudancas: false,
      investigacao_abranjente: false,
      decisao_modificar_manter_encerrar: false,
      investigacao_continua: false,
      revisao_diagnosticos_intervencoes: false,
      tabela_anotacao: [
        {
          nhb: "",
          diagnostico: "",
          resultado: "",
          intervencoes: [""],
        },
      ],
    });

    const addAnotacao = () => {
      // Adiciona um novo bloco com os campos pré-definidos
      avaliacao_enfermagem.value.tabela_anotacao.push({
        nhb: "",
        diagnostico: "",
        resultado: "",
        intervencoes: [""],
      });
    };

    const addIntervencao = (index) => {
      avaliacao_enfermagem.value.tabela_anotacao[index].intervencoes.push(""); // Adiciona uma nova intervenção vazia
    };

    const submitForm = async () => {
      console.log("Avaliação de Enfermagem criada:", avaliacao_enfermagem.value); // Verifica e exibe a avaliação

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

      // Verifica se a chave avaliacao_enfermagem existe, se não, cria-a
      if (!pacientes[pacienteIndex].avaliacao_enfermagem) {
        pacientes[pacienteIndex].avaliacao_enfermagem = []; // Inicializa como um array se não existir
      }

      // Adiciona a nova avaliação de enfermagem
      pacientes[pacienteIndex].avaliacao_enfermagem.push(avaliacao_enfermagem.value);

      // Atualiza a sessionStorage com a nova lista de pacientes
      sessionStorage.setItem("pacientes", JSON.stringify(pacientes));

      // Redireciona para a página de detalhes do paciente
      router.push(`/pacientes/${this.$route.params.id}/avaliacao`);
    };

    return {
      avaliacao_enfermagem,
      addAnotacao,
      addIntervencao,
      submitForm,
    };
  },
};
</script>

<style scoped>
/* Adicione qualquer estilo adicional que você precise aqui */
</style>
