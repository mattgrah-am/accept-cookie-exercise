<template>
  <div class="absolute bottom-0 w-full bg-black/75 py-8 text-center text-white">
    <h2 class="mb-4 text-2xl font-bold">Accet Cookies</h2>
    <div class="flex items-center justify-center gap-4">
      <button
        @click="handleCookieDecision(true)"
        class="rounded bg-green-700 px-4 py-2 font-bold shadow hover:bg-green-900"
      >
        (a)ccept
      </button>
      <button
        @click="handleCookieDecision(false)"
        class="rounded bg-red-700 px-4 py-2 font-bold shadow hover:bg-red-900"
      >
        (d)ecline
      </button>
    </div>
  </div>
</template>

<script setup lang="ts">
import { onMounted, onBeforeMount } from "vue";

const emit = defineEmits(["cookieAccepted", "cookieDeclined"]);

const handleCookieDecision = (cookieAccepted: boolean) => {
  if (cookieAccepted) {
    console.log("Cookies accepted");
    localStorage.setItem("acceptedCookie", "true");
    emit("cookieAccepted");
  } else {
    console.log("Cookies declined");
    localStorage.setItem("acceptedCookie", "false");
    emit("cookieDeclined");
  }
};

const handleKeyPress = (event: KeyboardEvent) => {
  if (event.key === "a") {
    handleCookieDecision(true);
  } else if (event.key === "d") {
    handleCookieDecision(false);
  }
};

onMounted(() => {
  const cookieState = localStorage.getItem("acceptedCookie");
  if (cookieState === "true") {
    emit("cookieAccepted");
  } else if (cookieState === "false") {
    emit("cookieDeclined");
  }
  document.addEventListener("keypress", handleKeyPress);
});

onBeforeMount(() => {
  document.removeEventListener("keypress", handleKeyPress);
});
</script>
