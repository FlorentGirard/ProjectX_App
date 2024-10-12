<template>
  <nav class="flex justify-between items-center">
    <h1 class="">ProjectX</h1>
    <UHorizontalNavigation :links="links" class="bg-slate-300 w-1/4" />
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
