<template>
  <td class="px-6 py-4 whitespace-nowrap">
    <div class="flex items-center">
      <div class="text-sm text-black font-medium">
        {{ name }}
      </div>
    </div>
  </td>
  <td class="px-6 text-left py-4 whitespace-nowrap">
    <div class="text-sm text-black font-medium">
      {{ surname }}
    </div>
  </td>
  <td class="px-6 text-left py-4 whitespace-nowrap">
    <div class="text-sm text-black font-medium">
      {{ age }}
    </div>
  </td>
  <td class="px-6 py-4 text-left whitespace-nowrap">
    <div class=" text-sm text-black font-medium">
      {{ city }}

      {{ flag }}
    </div>
  </td>
  <td class="px-6 py-4 text-left whitespace-nowrap">
    <div class="text-sm text-black font-medium">
      {{ address }}
    </div>
  </td>
</template>

<script>
export default {
  setup() {},
  props: ["name", "surname", "age", "city", "address", "flag"],
};
</script>

<style></style>
