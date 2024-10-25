<template>
  <div class="container mx-auto p-6">
    <h1 class="text-4xl font-bold text-indigo-600 mb-4">Adicionar Diagnóstico</h1>
    <form @submit.prevent="submitForm" class="space-y-4">
      <div>
        <label for="prontuario" class="block text-sm font-semibold text-gray-700">
          Número do Prontuário
        </label>
        <input
          v-model="diagnostico.prontuario"
          type="text"
          id="prontuario"
          required
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label for="problemasSaude" class="block text-sm font-semibold text-gray-700">
          Problemas de Saúde
        </label>
        <input
          v-model="diagnostico.problemas_saude"
          type="text"
          id="problemasSaude"
          required
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label for="riscos" class="block text-sm font-semibold text-gray-700">
          Riscos
        </label>
        <input
          v-model="diagnostico.riscos"
          type="text"
          id="riscos"
          required
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label for="sinaisSintomas" class="block text-sm font-semibold text-gray-700">
          Sinais ou Sintomas
        </label>
        <input
          v-model="diagnostico.sinais_ou_sintomas"
          type="text"
          id="sinaisSintomas"
          required
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label for="aprendizado" class="block text-sm font-semibold text-gray-700">
          Aprendizado
        </label>
        <input
          v-model="diagnostico.aprendizado"
          type="text"
          id="aprendizado"
          required
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label for="recursos" class="block text-sm font-semibold text-gray-700">
          Recursos
        </label>
        <input
          v-model="diagnostico.recursos"
          type="text"
          id="recursos"
          required
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label for="estadoSaude" class="block text-sm font-semibold text-gray-700">
          Estado de Saúde
        </label>
        <input
          v-model="diagnostico.estado_de_saude"
          type="text"
          id="estadoSaude"
          required
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <button
        @click="goBack()"
        class="mt-4 mr-4 bg-green-600 text-white font-semibold py-2 px-4 rounded hover:bg-green-700 transition-colors"
      >
        Voltar
      </button>
      <button
        type="submit"
        class="mt-4 bg-indigo-600 text-white font-semibold py-2 px-4 rounded hover:bg-indigo-700 transition-colors"
      >
        Adicionar Diagnóstico
      </button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      diagnostico: {
        prontuario: null, // Será definido quando você recuperar os dados do paciente
        problemas_saude: "",
        riscos: "",
        sinais_ou_sintomas: "",
        aprendizado: "",
        recursos: "",
        estado_de_saude: "",
      },
    };
  },
  methods: {
    async submitForm() {
      const storedPacientes = sessionStorage.getItem("pacientes");

      if (!storedPacientes) {
        console.error("Nenhum paciente encontrado na sessionStorage.");
        return;
      }

      const pacientes = JSON.parse(storedPacientes);
      const pacienteId = parseInt(this.$route.params.id);
      const pacienteIndex = pacientes.findIndex((item) => item.id === pacienteId);

      if (pacienteIndex === -1) {
        console.error("Paciente não encontrado.");
        return;
      }

      // Garante que o array de diagnósticos exista
      if (!pacientes[pacienteIndex].diagnosticos) {
        pacientes[pacienteIndex].diagnosticos = []; // Inicializa como um array se não existir
      }

      // Adiciona o novo diagnóstico ao array de diagnósticos do paciente
      const novoDiagnostico = {
        id: Date.now(), // Gera um ID único baseado no timestamp
        prontuario: pacienteId,
        ...this.diagnostico, // Espalha os dados do formulário
      };
      pacientes[pacienteIndex].diagnosticos.push(novoDiagnostico);

      console.log(pacientes[pacienteIndex]);

      // Armazena os pacientes atualizados de volta na sessionStorage
      sessionStorage.setItem("pacientes", JSON.stringify(pacientes));

      // Limpa o formulário
      this.diagnostico = {
        prontuario: null,
        problemas_saude: "",
        riscos: "",
        sinais_ou_sintomas: "",
        aprendizado: "",
        recursos: "",
        estado_de_saude: "",
      };

      // Redireciona para a página do paciente
      this.$router.push(`/pacientes/${pacienteId}/diagnosticos`);
    },
    goBack() {
      this.$router.push(`/pacientes/${this.$route.params.id}/diagnosticos`); // Redireciona de volta à lista de pacientes
    },
  },
};
</script>

<style scoped>
/* Adicione seu estilo aqui, se necessário */
</style>
