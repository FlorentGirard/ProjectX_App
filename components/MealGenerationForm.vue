<script setup lang="ts">
import { z } from 'zod'
import type { FormSubmitEvent } from '#ui/types'

const options = [
  { label: '1 Semaine', value: 1 },
  { label: '2 Semaines', value: 2 },
  { label: '3 Semaines', value: 3 },
  { label: '4 Semaines', value: 4 }
]

const schema = z.object({
  email: z.string().email('Invalid email'),
  password: z.string().min(8, 'Must be at least 8 characters')
})

type Schema = z.output<typeof schema>

const state = reactive({
  email: undefined,
  password: undefined,
  nbrSemaine: undefined,
})

async function onSubmit (event: FormSubmitEvent<Schema>) {
  // Do something with data
  console.log(event.data)
}
</script>

<template>
  <UForm :schema="schema" :state="state" class="space-y-4" @submit="onSubmit">
    <UFormGroup name="nbrSemaine" label="Sélectionnez le nombre de semaines à générer">
      <USelect v-model="state.nbrSemaine" placeholder="Select le nombre de semaines à générer." :options="options" />
    </UFormGroup>

    <UFormGroup label="Password" name="password">
      <USelect v-model="state.nbrSemaine" placeholder="Select le nombre de semaines à générer." :options="options" />
      <UInput v-model="state.input"  />
    </UFormGroup>

    <UButton type="submit">
      Voir mes Menus
    </UButton>
  </UForm>
</template>

