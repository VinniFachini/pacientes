<template>
  <div class="container mx-auto p-6">
    <h1 class="text-4xl font-bold text-indigo-600 mb-4">Criar Novo Histórico</h1>
    <form @submit.prevent="submitForm" class="space-y-4">
      <!-- Identificação -->
      <h2 class="text-2xl font-semibold text-gray-700 mb-2">Identificação</h2>
      <div>
        <label for="nome" class="block text-sm font-semibold text-gray-700">Nome</label>
        <input
          v-model="historico.identificacao.nome"
          type="text"
          id="nome"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label for="idade" class="block text-sm font-semibold text-gray-700">Idade</label>
        <input
          v-model="historico.identificacao.idade"
          type="number"
          id="idade"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label for="nascimento" class="block text-sm font-semibold text-gray-700"
          >Data de Nascimento</label
        >
        <input
          v-model="historico.identificacao.nascimento"
          type="date"
          id="nascimento"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label for="leito" class="block text-sm font-semibold text-gray-700">Leito</label>
        <input
          v-model="historico.identificacao.leito"
          type="number"
          id="leito"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label for="estado_civil" class="block text-sm font-semibold text-gray-700"
          >Estado Civil</label
        >
        <input
          v-model="historico.identificacao.estado_civil"
          type="text"
          id="estado_civil"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label for="filhos" class="block text-sm font-semibold text-gray-700"
          >Filhos (idades)</label
        >
        <input
          v-model="historico.identificacao.filhos"
          type="text"
          id="filhos"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
          placeholder="Ex: 12, 15"
        />
      </div>
      <div>
        <label for="genero" class="block text-sm font-semibold text-gray-700"
          >Gênero</label
        >
        <input
          v-model="historico.identificacao.genero"
          type="text"
          id="genero"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label for="escolaridade" class="block text-sm font-semibold text-gray-700"
          >Escolaridade</label
        >
        <input
          v-model="historico.identificacao.escolaridade"
          type="text"
          id="escolaridade"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label for="etnia" class="block text-sm font-semibold text-gray-700">Etnia</label>
        <input
          v-model="historico.identificacao.etnia"
          type="text"
          id="etnia"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label for="ocupacao" class="block text-sm font-semibold text-gray-700"
          >Ocupação</label
        >
        <input
          v-model="historico.identificacao.ocupacao"
          type="text"
          id="ocupacao"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label for="naturalidade" class="block text-sm font-semibold text-gray-700"
          >Naturalidade</label
        >
        <input
          v-model="historico.identificacao.naturalidade"
          type="text"
          id="naturalidade"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label for="procedencia" class="block text-sm font-semibold text-gray-700"
          >Procedência</label
        >
        <input
          v-model="historico.identificacao.procedencia"
          type="text"
          id="procedencia"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label for="religiao" class="block text-sm font-semibold text-gray-700"
          >Religião</label
        >
        <input
          v-model="historico.identificacao.religiao"
          type="text"
          id="religiao"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label for="cuidador" class="block text-sm font-semibold text-gray-700"
          >Cuidador</label
        >
        <select
          v-model="historico.identificacao.cuidador"
          id="cuidador"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        >
          <option value="Sim">Sim</option>
          <option value="Não">Não</option>
        </select>
      </div>
      <div>
        <label for="grupo_sanguineo" class="block text-sm font-semibold text-gray-700"
          >Grupo Sanguíneo</label
        >
        <input
          v-model="historico.identificacao.grupo_sanguineo"
          type="text"
          id="grupo_sanguineo"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label for="fator_rh" class="block text-sm font-semibold text-gray-700"
          >Fator RH</label
        >
        <input
          v-model="historico.identificacao.fator_rh"
          type="text"
          id="fator_rh"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>

      <h2 class="text-2xl font-semibold text-gray-800">
        Informações sobre Doença e Tratamento
      </h2>
      <div>
        <label for="motivo_internacao" class="block text-sm font-semibold text-gray-700"
          >Motivo da Internação</label
        >
        <input
          v-model="historico.informacoes_doenca_tratamento.motivo_internacao"
          type="text"
          id="motivo_internacao"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label for="diagnostico_medico" class="block text-sm font-semibold text-gray-700"
          >Diagnóstico Médico</label
        >
        <input
          v-model="historico.informacoes_doenca_tratamento.diagnostico_medico"
          type="text"
          id="diagnostico_medico"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label for="doencas_cronicas" class="block text-sm font-semibold text-gray-700"
          >Doenças Crônicas</label
        >
        <input
          v-model="historico.informacoes_doenca_tratamento.doencas_cronicas"
          type="text"
          id="doencas_cronicas"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label for="fatores_risco" class="block text-sm font-semibold text-gray-700"
          >Fatores de Risco</label
        >
        <input
          v-model="historico.informacoes_doenca_tratamento.fatores_risco"
          type="text"
          id="fatores_risco"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label for="cirurgias" class="block text-sm font-semibold text-gray-700"
          >Cirurgias</label
        >
        <input
          v-model="historico.informacoes_doenca_tratamento.cirurgias"
          type="text"
          id="cirurgias"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label for="outros_tratamentos" class="block text-sm font-semibold text-gray-700"
          >Outros Tratamentos</label
        >
        <input
          v-model="historico.informacoes_doenca_tratamento.outros_tratamentos"
          type="text"
          id="outros_tratamentos"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label
          for="alergias_medicamentos"
          class="block text-sm font-semibold text-gray-700"
          >Alergia a Medicamentos</label
        >
        <select
          v-model="historico.informacoes_doenca_tratamento.alergias_medicamentos"
          id="alergias_medicamentos"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        >
          <option value="true">Sim</option>
          <option value="false">Não</option>
        </select>
      </div>
      <div>
        <label for="especificar" class="block text-sm font-semibold text-gray-700"
          >Especificar</label
        >
        <input
          v-model="historico.informacoes_doenca_tratamento.especificar"
          type="text"
          id="especificar"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label
          for="tratamentos_anteriores"
          class="block text-sm font-semibold text-gray-700"
          >Tratamentos Anteriores</label
        >
        <input
          v-model="historico.informacoes_doenca_tratamento.tratamentos_anteriores"
          type="text"
          id="tratamentos_anteriores"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>

      <!-- Socioeconômicos Culturais -->
      <h2 class="text-2xl font-semibold text-gray-700 mt-4 mb-2">
        Socioeconômicos Culturais
      </h2>
      <div>
        <label for="moradia" class="block text-sm font-semibold text-gray-700"
          >Moradia</label
        >
        <input
          v-model="historico.socio_economicos_culturais.moradia"
          type="text"
          id="moradia"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label for="animais_domesticos" class="block text-sm font-semibold text-gray-700"
          >Animais Domésticos</label
        >
        <input
          v-model="historico.socio_economicos_culturais.animais_domesticos"
          type="text"
          id="animais_domesticos"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>

      <!-- Higiene -->
      <h2 class="text-2xl font-semibold text-gray-700 mt-4 mb-2">Higiene</h2>
      <div>
        <label for="habito_tomar_banho" class="block text-sm font-semibold text-gray-700"
          >Hábito de Tomar Banho</label
        >
        <input
          v-model="historico.higiene.habito_tomar_banho"
          type="text"
          id="habito_tomar_banho"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label
          for="atividade_fisica_trabalho"
          class="block text-sm font-semibold text-gray-700"
          >Atividade Física no Trabalho</label
        >
        <input
          v-model="historico.higiene.atividade_fisica_trabalho"
          type="text"
          id="atividade_fisica_trabalho"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label for="fumo" class="block text-sm font-semibold text-gray-700">Fumo</label>
        <input
          v-model="historico.higiene.fumo"
          type="text"
          id="fumo"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label for="alcool" class="block text-sm font-semibold text-gray-700"
          >Álcool</label
        >
        <input
          v-model="historico.higiene.alcool"
          type="text"
          id="alcool"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label for="sono_repouso" class="block text-sm font-semibold text-gray-700"
          >Sono Repouso</label
        >
        <input
          v-model="historico.higiene.sono_repouso"
          type="text"
          id="sono_repouso"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label for="exercicios_fisicos" class="block text-sm font-semibold text-gray-700"
          >Exercícios Físicos</label
        >
        <input
          v-model="historico.higiene.exercicios_fisicos"
          type="text"
          id="exercicios_fisicos"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label for="eliminacao_urinaria" class="block text-sm font-semibold text-gray-700"
          >Eliminação Urinaria</label
        >
        <input
          v-model="historico.higiene.eliminacao_urinaria"
          type="text"
          id="eliminacao_urinaria"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label
          for="eliminacoes_intestinais"
          class="block text-sm font-semibold text-gray-700"
          >Eliminação Intestinal</label
        >
        <input
          v-model="historico.higiene.eliminacoes_intestinais"
          type="text"
          id="eliminacoes_intestinais"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <!-- Outros campos de Higiene -->

      <button
        type="submit"
        class="mt-4 bg-indigo-600 text-white font-semibold py-2 px-4 rounded hover:bg-indigo-700 transition-colors"
      >
        Criar Histórico
      </button>
    </form>
  </div>
</template>

<script setup>
import { ref } from "vue";

const route = useRoute();
const router = useRouter();

// Inicialização do estado do histórico com campos específicos
const historico = ref({
  identificacao: {
    nome: "",
    idade: "",
    estado_civil: "",
    filhos: "",
    genero: "",
    escolaridade: "",
    etnia: "",
    ocupacao: "",
    naturalidade: "",
    procedencia: "",
    religiao: "",
    cuidador: "",
    grupo_sanguineo: "",
    fator_rh: "",
  },
  informacoes_doenca_tratamento: {
    motivo_internacao: "",
    diagnostico_medico: "",
    doencas_cronicas: "",
    fatores_risco: "",
    alergias_medicamentos: "",
    especificar: "",
    tratamentos_anteriores: "",
    cirurgias: "",
    outros_tratamentos: "",
  },
  socio_economicos_culturais: {
    moradia: "",
    animais_domesticos: "",
  },
  higiene: {
    habito_tomar_banho: "",
    atividade_fisica_trabalho: "",
    fumo: "",
    alcool: "",
    sono_repouso: "",
    exercicios_fisicos: "",
    eliminacao_urinaria: "",
    eliminacoes_intestinais: "",
  },
});

// Função para manipular o valor dos campos no objeto 'historico'
function atualizarCampo(categoria, campo, valor) {
  if (historico[categoria] && campo in historico[categoria]) {
    historico[categoria][campo] = valor;
  }
}

// Função para submissão dos dados do formulário
const submitForm = async () => {
  console.log("Histórico criado:", historico.value); // Verifica e exibe o histórico a ser criado

  const storedPacientes = sessionStorage.getItem("pacientes");

  if (!storedPacientes) {
    console.error("Nenhum paciente encontrado na sessionStorage.");
    return;
  }

  // Converte a lista de pacientes do sessionStorage
  const pacientes = JSON.parse(storedPacientes);

  // Obtém o ID do paciente da rota
  const pacienteId = parseInt(route.params.id);
  const pacienteIndex = pacientes.findIndex((item) => item.id === pacienteId);

  if (pacienteIndex === -1) {
    console.error("Paciente não encontrado.");
    return;
  }

  // Garante que o array de históricos exista
  if (!pacientes[pacienteIndex].historico) {
    pacientes[pacienteIndex].historico = []; // Inicializa como um array se não existir
  }

  // Adiciona o novo histórico ao array de históricos do paciente
  pacientes[pacienteIndex].historico = historico.value; // Adiciona o novo histórico ao array existente

  console.log(pacientes[pacienteIndex]);

  // Armazena os pacientes atualizados de volta na sessionStorage
  sessionStorage.setItem("pacientes", JSON.stringify(pacientes)); // Salva a lista atualizada de pacientes

  // Redireciona para a página do paciente
  router.push(`/pacientes/${pacienteId}/historico`);
};
</script>
