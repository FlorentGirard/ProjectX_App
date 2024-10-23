<template>
  <nav class="flex justify-between items-center mt-2">
    <h1 class="ml-28">ProjectX</h1>
    <UHorizontalNavigation :links="links" class="w-1/4" />
  </nav>
</template>

<script setup lang="ts">
const links = [
  {
    label: "Planning",
    to: "/",
  },
  {
    label: "Liste repas",
    to: "/test",
  },
  {
    label: "Ajouter Repas",
    to: "/test",
  },
];
</script>
