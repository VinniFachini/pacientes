<template>
  <div class="container mx-auto p-6">
    <h1 class="text-4xl font-bold text-indigo-600 mb-4">Criar Novo Prontuário</h1>
    <form @submit.prevent="submitForm" class="space-y-4">
      <div>
        <label for="pa" class="block text-sm font-semibold text-gray-700">Nome</label>
        <input
          v-model="novoPaciente.nome"
          type="text"
          id="nome"
          required
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label for="pa" class="block text-sm font-semibold text-gray-700"
          >CPF (Apenas Números)</label
        >
        <input
          v-model="novoPaciente.cpf"
          type="text"
          id="cpf"
          required
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label for="pa" class="block text-sm font-semibold text-gray-700"
          >Nascimento</label
        >
        <input
          v-model="novoPaciente.nascimento"
          type="date"
          id="nascimento"
          required
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>

      <button
        type="submit"
        class="mt-4 bg-indigo-600 text-white font-semibold py-2 px-4 rounded hover:bg-indigo-700 transition-colors"
      >
        Criar Paciente
      </button>
    </form>
  </div>
</template>

<script setup>
import { ref } from "vue";

const route = useRoute();
const router = useRouter();
const paciente = ref(null);

const novoPaciente = ref({
  id: "",
  nome: "",
  cpf: "",
  nascimento: "",
});

onMounted(() => {
  // Recupera os dados do SessionStorage
  const storedPacientes = sessionStorage.getItem("pacientes");
  const pacienteId = parseInt(route.params.id); // Obtém o ID do paciente da rota

  if (storedPacientes) {
    const pacientes = JSON.parse(storedPacientes);
    // Busca o paciente pelo ID
    paciente.value = pacientes.find((item) => item.id === pacienteId);
    console.log(paciente.value);
  }
});

const submitForm = async () => {
  // Ajuste de nome para consistência
  const pacienteNovo = novoPaciente.value;

  console.log("Paciente criado:", pacienteNovo);

  let storedPacientes = sessionStorage.getItem("pacientes");

  if (!storedPacientes) {
    console.error("Nenhum paciente encontrado na sessionStorage.");
    storedPacientes = "[]"; // Define como string de array vazio para inicializar
  }

  // Recupera os pacientes ou cria array vazio
  const pacientes = JSON.parse(storedPacientes) || [];

  // Atribui um ID ao novo paciente
  pacienteNovo.id = pacientes.length ? pacientes.length + 1 : 1;

  // Adiciona o novo paciente ao array
  pacientes.push(pacienteNovo);

  console.log("Lista de pacientes atualizada:", pacientes);

  // Salva a lista de pacientes atualizada no sessionStorage
  sessionStorage.setItem("pacientes", JSON.stringify(pacientes));

  router.push("/pacientes");
};
</script>

<style scoped>
/* Estilos adicionais, se necessário */
</style>
