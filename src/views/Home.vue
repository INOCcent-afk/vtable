<template>
  <div class="flex items-center justify-center h-screen w-screen">
    <div
      class="topBackground bg-purple-600 fixed  w-screen top-0 rounded-b-full"
    ></div>
    <div
      class="fixed top-5 left-5 bg-purple-400 w-10 h-10 rounded-full flex cursor-pointer items-center justify-center"
    >
      <MoonIcon
        v-if="theme === 'light'"
        class="w-5 fill-current text-purple-700"
      />
      <SunIcon v-else class="w-5 fill-current text-purple-700" />
    </div>
    <Datatable />
  </div>
</template>

<script>
import { ref } from "@vue/reactivity";

import Datatable from "../Containers/Datatable.vue";
import { MoonIcon } from "@heroicons/vue/solid";
import { SunIcon } from "@heroicons/vue/solid";

export default {
  name: "Home",
  setup() {
    const theme = ref("light");
    const colorTheme = ref(theme.value === "light" ? "dark" : "light");

    return {
      colorTheme,
      theme,
    };
  },
  components: {
    Datatable,
    MoonIcon,
    SunIcon,
  },
};
</script>

<style scoped>
.topBackground {
  height: 60vh;
}
</style>
