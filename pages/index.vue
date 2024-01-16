<template>
  <div>
    <ClientOnly>
      <AppCalendar />
    </ClientOnly>
  </div>
</template>

<script setup>
import AppCalendar from "~/components/app-calendar.vue";
</script>