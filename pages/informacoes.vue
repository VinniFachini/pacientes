<template>
  <div class="flex flex-col items-center min-h-screen">
    <Header />
    <section
      class="main-content flex-grow flex flex-col items-center justify-start p-20 max-w-4xl"
    >
      <h2 class="text-4xl font-semibold text-gray-800 mb-4">Informações</h2>
      <NuxtLink
        target="_blank"
        class="bg-slate-600 hover:bg-blue-500 transition-colors px-5 py-3 text-white rounded-md mb-4 w-full"
        to="https://biblioteca.cofen.gov.br/wp-content/uploads/2020/09/manual-procedimento-operacional-padrao-servico-enfermagem.pdf"
        >Procedimento Operacional Padrão (POP)</NuxtLink
      >
      <NuxtLink
        target="_blank"
        class="bg-slate-600 hover:bg-blue-500 transition-colors px-5 py-3 text-white rounded-md mb-4 w-full"
        to="https://www.coren-ba.gov.br/wp-content/uploads/2016/07/GUIA_PRATICO_148X210_COREN.pdf"
        >Sistematização da Assistência de Enfermagem (SAE)</NuxtLink
      >
      <NuxtLink
        target="_blank"
        class="bg-slate-600 hover:bg-blue-500 transition-colors px-5 py-3 text-white rounded-md mb-4 w-full"
        to="https://portal.coren-sp.gov.br/wp-content/uploads/2022/09/anotacao-de-enfermagem.pdf"
        >Relatório de Enfermagem
      </NuxtLink>
    </section>
    <Footer />
  </div>
</template>
