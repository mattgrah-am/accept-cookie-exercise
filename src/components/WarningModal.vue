<template>
  <div class="z-99 absolute h-screen w-screen bg-black/75">
    <div
      class="absolute left-1/2 top-1/2 max-w-sm -translate-x-1/2 -translate-y-1/2 transform rounded-lg border bg-white p-8 text-center shadow-lg"
    >
      <h2 class="mb-4 text-2xl font-bold">
        You must accept cookies to access this sites content
      </h2>
      <button
        @click="emit('close')"
        class="rounded bg-red-700 px-4 py-2 font-bold text-white shadow hover:bg-red-900"
      >
        Close
      </button>
    </div>
  </div>
</template>

<script setup lang="ts">
const emit = defineEmits(["close"]);
</script>
