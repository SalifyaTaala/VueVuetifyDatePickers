<template>
  <v-app>
    <v-main>
      <SelectItem />
    </v-main>
  </v-app>
</template>

<script lang="ts">
import { Vue, Component } from "vue-property-decorator";
import SelectItem from "./components/Selected.vue";
@Component({
  components: { SelectItem }
})
export default class App extends Vue {}
</script>
