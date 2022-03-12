<template>
  <v-app-bar
    color="#005eb8"
    dark
    style="color:white;"
  >
    <v-spacer></v-spacer>
    <v-btn 
      @click="drawerFilters=!drawerFilters"
      variant="text"
      icon="mdi-tune-vertical"
    ></v-btn>
  </v-app-bar>

  <Filters
    :open="drawerFilters"
    @close="drawerFilters=false"
  ></Filters>
</template>

<script lang="ts">
import { defineComponent, defineAsyncComponent, ref } from "vue";

export default defineComponent({
  name: "AppBar",
  components: {
    Filters : defineAsyncComponent(() => import('@/components/common/Filters.vue')),
  },
  props: {},
  setup() {
    let drawerFilters = ref(false);

    return {
      drawerFilters,
    };
  },
});
</script>

<style scoped>

</style>
