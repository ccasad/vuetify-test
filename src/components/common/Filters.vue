<template>
  <v-navigation-drawer
    v-model="drawer"
    width="300"
    position="right"
    temporary
  >
    <v-container fluid class="mt-1">
      <v-row v-if="states" class="mt-2">
        <v-col class="text-left">
          This v-select is supposed to show the states when you 
          click on it, but nothing is displayed.<br/>
          <v-select
            v-model="selectedStates"
            :items="states"
            label="States"
            density="compact"
            multiple
            hide-details
            class="mt-2"
          ></v-select>
        </v-col>
      </v-row>
    </v-container>

  </v-navigation-drawer>
</template>

<script lang="ts">
import { defineComponent, watch, ref, computed } from "vue";

import { US_STATES } from "@/common/constants";

const EMITTED_ACTIONS = {
  CLOSE: "close",
};

export default defineComponent({
  name: "Filters",
  props: {
    open: {
      type: Boolean,
    },
  },
  setup(props:any, context:any) {
    let drawer = ref(false);
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

    const handleToggleDrawer = (value:boolean) => {
      drawer.value = value;
    };

    watch(() => props.open, () => drawer.value = props.open);

    watch(drawer, () => {
      if (!drawer.value) {
        context.emit(EMITTED_ACTIONS.CLOSE);
      }
    });

    return {
      drawer,
      selectedStates,
      states,
      handleToggleDrawer,
    };
  },
});
</script>

<style>
.division-btns.v-btn-group .v-btn:not(:last-child) {
  border-right-width: thin !important;
  border-right-style: solid !important;
  border-right-color: rgb(197, 197, 197) !important;
}
</style>

<style scoped>

</style>