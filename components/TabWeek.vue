<script setup lang="ts">
const items = [
  {
    key: "week1",
    label: "Semaine 1 ",
  },
  {
    key: "week2",
    label: "Semaine 2 ",
  },
  {
    key: "week3",
    label: "Semaine 3 ",
  },
  {
    key: "week4",
    label: "Semaine 4 ",
  },
];

const accountForm = reactive({ name: "Benjamin", username: "benjamincanac" });
const passwordForm = reactive({ currentPassword: "", newPassword: "" });
</script>

<template>
  <UTabs :items="items" class="w-full">
    <template #item="{ item }">
      <UCard>
        <template #header>
          <p
            class="text-base font-semibold leading-6 text-gray-900 dark:text-white"
          >
            {{ item.label }}
          </p>
        </template>
        <TableMealWeak />

        <!-- <div v-if="item.key === 'week1'" class="space-y-3">
                <TableMealWeak />

        </div>
        <div v-else-if="item.key === 'week2'" class="space-y-3">
          <TableMealWeak />
        </div> -->

        <!--   <template #footer>
            <UButton type="submit" color="black">
              Save {{ item.key === 'account' ? 'account' : 'password' }}
            </UButton>
          </template> -->
      </UCard>
    </template>
  </UTabs>
</template>
