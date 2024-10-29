<template>
  <div class="flex flex-col min-h-screen">
    <header class="bg-gray-800 text-white p-4 text-center">
      <nav>
        <NuxtLink to="/" class="text-white hover:text-indigo-400 mx-4"
          >Página Inicial</NuxtLink
        >
        <NuxtLink to="/pacientes" class="text-white hover:text-indigo-400 mx-4"
          >Pacientes</NuxtLink
        >
      </nav>
    </header>

    <section class="main-content flex-grow flex flex-col items-center justify-center p-6">
      <div class="image-container mb-6">
        <img
          src="https://www.etecamimjundi.com.br/assets/img/logo-etec.png"
          alt="Logo ETEC Amim Jundi"
          class="w-9/12 h-auto"
        />
      </div>
      <div class="presentation text-center">
        <h2 class="text-4xl font-semibold text-gray-800 mb-4">Agradecimentos</h2>
        <p class="text-gray-600 text-2xl max-w-4xl">
          Somos gratos aos nossos professores e colegas por todo o apoio durante o
          desenvolvimento deste trabalho. Agradecemos também à ETEC Amim Jundi por nos
          proporcionar um ambiente de aprendizado inspirador.
        </p>
      </div>
    </section>

    <footer class="bg-gray-800 text-white p-4 text-center">
      <p>&copy; 2024 - Trabalho de Conclusão de Curso - ETEC Amim Jundi</p>
    </footer>
  </div>
</template>

<script>
export default {
  name: "ThankYouPage",
};
</script>

<style scoped>
/* Estilos adicionais, se necessário */
</style>
