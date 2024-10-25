<template>
  <div class="container mx-auto p-6">
    <h1 class="text-4xl font-bold text-indigo-600 mb-4">Criar Novo Prontuário</h1>
    <form @submit.prevent="submitForm" class="space-y-4">
      <div>
        <label for="pa" class="block text-sm font-semibold text-gray-700"
          >Pressão Arterial (PA)</label
        >
        <input
          v-model="novoProntuario.pa"
          type="text"
          id="pa"
          required
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label for="fr" class="block text-sm font-semibold text-gray-700"
          >Frequência Respiratória (FR)</label
        >
        <input
          v-model="novoProntuario.fr"
          type="number"
          id="fr"
          required
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label for="fc" class="block text-sm font-semibold text-gray-700"
          >Frequência Cardíaca (FC)</label
        >
        <input
          v-model="novoProntuario.fc"
          type="number"
          id="fc"
          required
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label for="temperatura" class="block text-sm font-semibold text-gray-700"
          >Temperatura</label
        >
        <input
          v-model="novoProntuario.temperatura"
          type="text"
          id="temperatura"
          required
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label for="spo2" class="block text-sm font-semibold text-gray-700">SPO2</label>
        <input
          v-model="novoProntuario.spo2"
          type="number"
          id="spo2"
          required
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label for="dextro" class="block text-sm font-semibold text-gray-700"
          >Dextro</label
        >
        <input
          v-model="novoProntuario.dextro"
          type="text"
          id="dextro"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label for="altura" class="block text-sm font-semibold text-gray-700"
          >Altura (cm)</label
        >
        <input
          v-model="novoProntuario.altura"
          type="number"
          id="altura"
          required
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label for="peso" class="block text-sm font-semibold text-gray-700"
          >Peso (kg)</label
        >
        <input
          v-model="novoProntuario.peso"
          type="number"
          id="peso"
          step="0.1"
          required
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label for="glasgow" class="block text-sm font-semibold text-gray-700"
          >Glasgow</label
        >
        <input
          v-model="novoProntuario.glasgow"
          type="text"
          id="glasgow"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label for="deambula" class="block text-sm font-semibold text-gray-700"
          >Deambulação</label
        >
        <select
          v-model="novoProntuario.deambula"
          id="deambula"
          required
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        >
          <option value="Sim">Sim</option>
          <option value="Não">Não</option>
        </select>
      </div>
      <div>
        <label for="diurese" class="block text-sm font-semibold text-gray-700"
          >Diurese</label
        >
        <input
          v-model="novoProntuario.diurese"
          type="text"
          id="diurese"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label for="evacuacao" class="block text-sm font-semibold text-gray-700"
          >Evacuação</label
        >
        <input
          v-model="novoProntuario.evacucao"
          type="text"
          id="evacuacao"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label for="alimentacao" class="block text-sm font-semibold text-gray-700"
          >Alimentação</label
        >
        <input
          v-model="novoProntuario.alimentacao"
          type="text"
          id="alimentacao"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label for="admissao" class="block text-sm font-semibold text-gray-700"
          >Admissão</label
        >
        <input
          v-model="novoProntuario.admissao"
          type="text"
          id="admissao"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label for="evolucao" class="block text-sm font-semibold text-gray-700"
          >Evolução</label
        >
        <input
          v-model="novoProntuario.evolucao"
          type="text"
          id="evolucao"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>

      <button
        type="submit"
        class="mt-4 bg-indigo-600 text-white font-semibold py-2 px-4 rounded hover:bg-indigo-700 transition-colors"
      >
        Criar Prontuário
      </button>
    </form>
  </div>
</template>

<script setup>
import { ref } from "vue";

const paciente = ref(null); // Armazena os dados do paciente
const route = useRoute();
const router = useRouter();

const novoProntuario = ref({
  id: paciente.value,
  pa: "",
  fr: "",
  fc: "",
  temperatura: "",
  spo2: "",
  dextro: "",
  altura: "",
  peso: "",
  glasgow: "",
  deambula: "Sim",
  diurese: "",
  evacuacao: "",
  alimentacao: "",
  admissao: "",
  evolucao: "",
});

onMounted(() => {
  // Recupera os dados do SessionStorage
  const storedPacientes = sessionStorage.getItem("pacientes");
  const pacienteId = parseInt(route.params.id); // Obtém o ID do paciente da rota

  if (storedPacientes) {
    const pacientes = JSON.parse(storedPacientes);
    // Busca o paciente pelo ID
    paciente.value = pacientes.find((item) => item.id === pacienteId).prontuarios;
    console.log(paciente.value);
  }
});
const submitForm = async () => {
  console.log("Prontuário criado:", novoProntuario.value); // Verifica e exibe o prontuário a ser criado

  const storedPacientes = sessionStorage.getItem("pacientes");

  if (!storedPacientes) {
    console.error("Nenhum paciente encontrado na sessionStorage.");
    return;
  }

  // Converte a lista de pacientes do sessionStorage
  const pacientes = JSON.parse(storedPacientes);

  // Obtém o ID do paciente da rota
  const pacienteId = parseInt(route.params.id);
  const paciente = pacientes.find((item) => item.id === pacienteId);

  if (!paciente) {
    console.error("Paciente não encontrado.");
    return;
  }

  // Garante que o array de prontuários exista
  if (!paciente.prontuarios) {
    paciente.prontuarios = [];
  }

  // Define o id do novo prontuário
  novoProntuario.value.id = paciente.prontuarios.length + 1;

  // Adiciona o novo prontuário ao array de prontuários do paciente
  paciente.prontuarios.push(await novoProntuario.value);

  // Armazena os pacientes atualizados de volta na sessionStorage
  sessionStorage.setItem("pacientes", JSON.stringify(pacientes));

  // Redireciona para a página do paciente
  router.push(`/pacientes/${pacienteId}`);
};
</script>

<style scoped>
/* Estilos adicionais, se necessário */
</style>
