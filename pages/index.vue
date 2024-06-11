<template>
  <div>
    <NuxtLink to="/hello">Visit hello page</NuxtLink>

    <ClientOnly>
      <AppCalendar />
    </ClientOnly>
  </div>
</template>

<script setup>
import AppCalendar from "~/components/app-calendar.vue";
</script>
