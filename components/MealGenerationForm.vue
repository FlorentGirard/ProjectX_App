<script setup lang="ts">
import { z } from "zod";
import type { FormSubmitEvent } from "#ui/types";

const options = [
  { label: "1 Semaine", value: 1 },
  { label: "2 Semaines", value: 2 },
  { label: "3 Semaines", value: 3 },
  { label: "4 Semaines", value: 4 },
];
//TODO Dynamiser with DB
const ingredientList = [
  { label: "Pâte", value: "pata" },
  { label: "Riz", value: "rice" },
];

const schema = z.object({
  email: z.string().email("Invalid email"),
  password: z.string().min(8, "Must be at least 8 characters"),
});

type Schema = z.output<typeof schema>;

const state = reactive({
  email: undefined,
  password: undefined,
  nbrSemaine: undefined,
  selectIngredient: [],
});

const addIngredientLimit = () => {
  state.selectIngredient.push({});
  console.log(state.selectIngredient.length);
};

const removeIngredientLimit = () => {
  state.selectIngredient.length -= 1;
};

async function onSubmit(event: FormSubmitEvent<Schema>) {
  // Do something with data
  console.log(event.data);
}
</script>

<template>
  <UForm :schema="schema" :state="state" class="space-y-4" @submit="onSubmit">
    <UFormGroup
      name="nbrSemaine"
      label="Sélectionnez le nombre de semaines à générer"
    >
      <USelect
        v-model="state.nbrSemaine"
        placeholder="Select le nombre de semaines à générer."
        :options="options"
      />
    </UFormGroup>

    <div class="flex justify-between">
      <h2>Personnaliser vos repas en limitant ou excluant certains aliments</h2>
      <UButton
        @click="addIngredientLimit"
        :disabled="state.selectIngredient.length === ingredientList.length"
        >Ajouter</UButton
      >
    </div>

    <UFormGroup
      label="SelectIngredient"
      name="selectIngredient"
      v-if="state.selectIngredient.length > 0"
    >
      <div
        class="flex mb-3"
        v-for="(ingredient, index) in state.selectIngredient"
        :key="index"
      >
        <USelect
          v-model="state.selectIngredient.ingredient"
          placeholder="Sélectionner ingrédient"
          :options="ingredientList"
          class="w-1/2"
        />
        <UInput v-model="state.selectIngredient.limit" class="w-1/2 ml-2" />
        <UButton
          icon="i-heroicons-trash"
          size="sm"
          color="red"
          square
          variant="link"
          @click="removeIngredientLimit"
        />
      </div>
    </UFormGroup>

    <UButton type="submit"> Voir mes Menus </UButton>
  </UForm>
</template>
