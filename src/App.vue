<template>
  <div
    class="min-h-screen flex items-center justify-center bg-gradient-to-r from-blue-500 via-purple-500 to-pink-500 p-6"
  >
    <div class="bg-white p-8 rounded-lg shadow-md w-full max-w-md">
      <h1 class="text-2xl font-bold mb-6 text-center">
        Inscrição para Encontro de Solteiros
      </h1>
      <div
        class="bg-yellow-100 border-l-4 border-yellow-500 text-yellow-700 p-4 mb-6"
        role="alert"
      >
        <p class="font-bold">Valor da inscrição:</p>
        <p class="text-2xl">60 reais</p>
      </div>
      <div
        class="bg-green-100 border-l-4 border-green-500 text-green-700 p-4 mb-6"
        role="alert"
      >
        <p class="font-bold">Chave Pix para pagamento:</p>
        <p class="text-2xl">039.706.772-03</p>
        <p class="text-2x5 font-bold">Evelyn Arlane Farias Silva</p>
      </div>
      <div
        class="bg-red-100 border-l-4 border-red-500 text-red-700 p-4 mb-6"
        role="alert"
      >
        <p class="font-bold">Atenção:</p>
        <p>
          Apos enviar essa inscrição, você irá ser redirecionado para o
          WhatsApp. Envie para o contato que você for redirecionado a imagem do
          comprovante de pagamento. Sua inscrição só será realizada se você
          mandar o comprovante de pagamento, caso não envie sua inscrição não
          será realizada.
        </p>
      </div>
      <form @submit.prevent="handleSubmit">
        <div class="mb-4">
          <label for="name" class="block text-gray-700">Nome Completo:</label>
          <input
            v-model="form.name"
            type="text"
            id="name"
            class="mt-1 p-2 w-full border rounded-md"
            required
          />
        </div>
        <div class="mb-4">
          <label for="age" class="block text-gray-700">Idade:</label>
          <input
            v-model="form.age"
            type="number"
            id="age"
            class="mt-1 p-2 w-full border rounded-md"
            required
          />
        </div>
        <div class="mb-4">
          <label for="church" class="block text-gray-700">Igreja:</label>
          <input
            v-model="form.church"
            type="text"
            id="church"
            class="mt-1 p-2 w-full border rounded-md"
            required
          />
        </div>
        <div class="mb-4">
          <label for="phone" class="block text-gray-700">Telefone:</label>
          <input
            v-model="form.phone"
            type="tel"
            id="phone"
            class="mt-1 p-2 w-full border rounded-md"
            required
          />
        </div>
        <button
          type="submit"
          class="w-full bg-blue-500 text-white py-2 rounded-md hover:bg-blue-600 transition-colors"
        >
          Enviar Inscrição
        </button>
      </form>
    </div>
  </div>
</template>

<script setup>
import { reactive } from "vue";

const form = reactive({
  name: "",
  age: "",
  church: "",
  phone: "",
});

const handleSubmit = () => {
  const whatsappURL = generateWhatsappURL();
  window.open(whatsappURL, "_blank");
};

const generateWhatsappURL = () => {
  const baseUrl = "https://wa.me/55"; // Prefixo do WhatsApp com código do país
  const phone = "6899907875"; // Número do telefone para o qual enviar a mensagem
  const text = `
Nome Completo: ${form.name}
Idade: ${form.age}
Igreja: ${form.church}
Telefone: ${form.phone}
  `;
  return `${baseUrl}${phone}?text=${encodeURIComponent(text.trim())}`;
};
</script>

<style scoped>
/* Adicione quaisquer estilos específicos para este componente aqui */
</style>
