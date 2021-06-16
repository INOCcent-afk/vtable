<template>
  <div class="absolute py-5 rounded-md shadow-2xl bg-white top-14 left-5">
    <p @click="$emit('noSort')" class="border-b p-2 px-5 hover:bg-purple-100">
      No Sort
    </p>
    <p
      @click="$emit('sortAscending')"
      class="border-b p-2 px-5 hover:bg-purple-100"
    >
      Sort Ascending
    </p>
    <p
      @click="$emit('sortDescending')"
      class="border-b py-2 px-5 hover:bg-purple-100"
    >
      Sort Descending
    </p>
  </div>
</template>

<script>
export default {
  emits: ["noSort", "sortAscending", "sortDescending"],
};
</script>

<style></style>
