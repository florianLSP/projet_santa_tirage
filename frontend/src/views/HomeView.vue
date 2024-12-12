<script setup lang="ts">
import { ref, watch } from 'vue'
import type { Ref } from 'vue'
import { TrashIcon } from '@heroicons/vue/20/solid'

const nbParticipant = ref(0)
const participants: Ref<Array<string>> = ref([])

function deleteParticipant(index: number) {
  participants.value.splice(index, 1)
  nbParticipant.value = participants.value.length
}

watch(nbParticipant, (newValue, oldValue) => {
  if (newValue > oldValue) {
    for (let i = oldValue; i < newValue; i++) {
      participants.value.push(`Participant ${i + 1}`)
    }
  } else if (newValue < oldValue) {
    participants.value.splice(newValue)
  }
})
</script>

<template>
  <div class="flex justify-center">
    <div class="flex flex-col">
      <h1 class="p-10 text-5xl">Qui offre quoi ?</h1>

      <div class="flex items-center space-x-4">
        <label for="nbParticipants">Sélectionnez le nombre de participants:</label>
        <input
          type="number"
          class="w-20 bg-transparent placeholder:text-slate-400 text-slate-700 text-sm border border-slate-200 rounded-md px-3 py-2 transition duration-300 ease focus:outline-none focus:border-slate-400 hover:border-slate-300 shadow-sm focus:shadow"
          v-model="nbParticipant"
        />
      </div>

      <div v-if="participants.length > 0" class="flex flex-col">
        <div
          v-for="(participant, index) in participants"
          :key="index"
          class="flex items-center space-x-4 mt-5"
        >
          <input
            type="text"
            class="w-64 bg-transparent placeholder:text-slate-400 text-slate-700 text-sm border border-slate-200 rounded-md px-3 py-2 transition duration-300 ease focus:outline-none focus:border-slate-400 hover:border-slate-300 shadow-sm focus:shadow"
            :placeholder="participant"
          />

          <button
            @click="deleteParticipant(index)"
            class="flex items-center justify-center rounded-md bg-red-600 p-2 text-white hover:bg-red-800 focus:outline-none focus:ring-2 focus:ring-red-600"
          >
            <TrashIcon class="h-5 w-5" />
          </button>
        </div>
      </div>
    </div>
  </div>
</template>
