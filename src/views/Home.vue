<template>
  <v-container fluid class="mt-5">
    <v-row v-if="states">
      <v-col cols="4" class="text-left"> 
        This v-select below shows all the states when you click on it. 
        But if you click on the filter button at the top right, the 
        v-select within v-navigation-drawer does not show the state 
        when you click on it.<br/>
        <v-select
          v-model="selectedStates"
          :items="states"
          label="States"
          class="mt-2"
        ></v-select>
      </v-col>
    </v-row>
  </v-container>
</template>

<script lang="ts">
import { defineComponent, ref, computed } from "vue";

import { US_STATES } from "@/common/constants";

export default defineComponent({
  name: "Home",
  components: {},
  props: {},
  setup() {
    let selectedStates:any = ref([]);

    const states:any = computed(() => {
      const arr:any = [];
      US_STATES.forEach((state:any) => {
        arr.push({
          title: state.name,
          value: state.code,
        });
      });
      return arr;
    });

    return {
      selectedStates,
      states,
    };
  },
});
</script>

<style scoped>

</style>