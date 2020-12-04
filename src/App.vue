<template>
  <v-app>
    <v-main>
      <FormatedDate />
    </v-main>
  </v-app>
</template>

<script lang="ts">
import { Vue, Component } from "vue-property-decorator";
import FormatedDate from "./components/formatedDate.vue";
@Component({
  components: { FormatedDate }
})
export default class App extends Vue {}
</script>
