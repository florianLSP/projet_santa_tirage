<script setup lang="ts">

</script>

<template>
  <div class="flex justify-center">
    <div class="flex flex-col">
      <h1 class="p-10 text-5xl">Qui offre quoi ?</h1>

      <div class="flex items-center space-x-4">
        <label for="">Sélectionnez le nombre de participant:</label>
        <input
          type="number"
          class="w-20 bg-transparent placeholder:text-slate-400 text-slate-700 text-sm border border-slate-200 rounded-md px-3 py-2 transition duration-300 ease focus:outline-none focus:border-slate-400 hover:border-slate-300 shadow-sm focus:shadow"
          value="0"
        />
      </div>
    </div>
  </div>
</template>
