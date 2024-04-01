<template>
  <div
    class="mx-auto grid h-screen max-w-screen-sm place-items-center font-sans"
  >
    <div
      class="rounded-xl border border-gray-200 p-8 shadow"
      v-if="cookieState"
    >
      <h1 class="mb-2 text-3xl font-bold">
        This is hidden by a cookie paywall
      </h1>
      <p class="text-lg">
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Nostrum
        praesentium quos ducimus mollitia tenetur eligendi, provident facilis
        fugit eum ea voluptatum tempora recusandae voluptates ipsum iste
        similique odit assumenda deleniti!
      </p>
    </div>
    <CookieNotice
      v-if="!cookieState"
      @cookie-accepted="cookieState = true"
      @cookie-declined="
        {
          cookieState = false;
          showWarning = true;
        }
      "
    />
    <WarningModal v-if="showWarning" @close="showWarning = false" />
  </div>
</template>

<script setup lang="ts">
import CookieNotice from "./components/CookieNotice.vue";
import WarningModal from "./components/WarningModal.vue";
import { ref } from "vue";

const showWarning = ref(false);
const cookieState = ref(false);
</script>
