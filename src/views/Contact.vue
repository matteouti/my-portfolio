<template>
  <section class="max-w-2xl mx-auto py-20 px-4 relative z-10">
    <h2 class="text-4xl font-bold mb-6 text-center">Contactez-moi</h2>

    <form @submit.prevent="handleSubmit">
      <input 
        v-model="form.name" 
        type="text" 
        name="name" 
        placeholder="Nom" 
        required
        class="w-full p-3 mb-4 border rounded-lg bg-gray-800 text-gray-100 border-gray-700 focus:ring-2 focus:ring-yellow-400 outline-none"
      />
      <input 
        v-model="form.email" 
        type="email" 
        name="email" 
        placeholder="Email" 
        required
        class="w-full p-3 mb-4 border rounded-lg bg-gray-800 text-gray-100 border-gray-700 focus:ring-2 focus:ring-yellow-400 outline-none"
      />
      <textarea 
        v-model="form.message" 
        name="message" 
        placeholder="Message" 
        required
        class="w-full p-3 mb-4 border rounded-lg h-32 bg-gray-800 text-gray-100 border-gray-700 focus:ring-2 focus:ring-yellow-400 outline-none"
      ></textarea>
      <button 
        type="submit" 
        class="bg-yellow-400 text-gray-900 px-6 py-3 rounded-lg hover:bg-yellow-500 transition transform hover:scale-105"
      >
        Envoyer
      </button>
    </form>

    <!-- ✅ Toast Notification (en haut) -->
    <transition name="slide-down">
      <div
        v-if="notification"
        class="fixed top-5 left-1/2 transform -translate-x-1/2 px-6 py-3 rounded-lg shadow-lg text-white text-sm md:text-base z-50"
        :class="success ? 'bg-green-600' : 'bg-red-600'"
      >
        {{ notification }}
      </div>
    </transition>
  </section>
</template>

<script setup>
import { ref } from "vue";

const form = ref({ name: "", email: "", message: "" });
const notification = ref("");
const success = ref(false);

const handleSubmit = async () => {
  try {
    const response = await fetch("https://formspree.io/f/meolbrzj", {
      method: "POST",
      headers: { "Content-Type": "application/json" },
      body: JSON.stringify(form.value),
    });

    if (response.ok) {
      notification.value = "✅ Message envoyé avec succès !";
      success.value = true;
      form.value = { name: "", email: "", message: "" }; // reset form
    } else {
      notification.value = "❌ Une erreur est survenue. Réessayez.";
      success.value = false;
    }
  } catch (error) {
    notification.value = "⚠️ Impossible d’envoyer le message.";
    success.value = false;
  }

  // Effacer la notif après 5s
  setTimeout(() => (notification.value = ""), 5000);
};
</script>

<style scoped>
/* Animation pour le toast en haut */
.slide-down-enter-active {
  transition: all 0.5s ease;
}
.slide-down-leave-active {
  transition: all 0.5s ease;
}
.slide-down-enter-from,
.slide-down-leave-to {
  opacity: 0;
  transform: translateY(-20px);
}
</style>
