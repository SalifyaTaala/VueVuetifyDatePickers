<template>
<div>
  <v-app>
    <v-main>
      <FormatedDate />
    </v-main>
  </v-app>
</div>
</template>

<script lang="ts">
import { Vue, Component } from "vue-property-decorator";
import FormatedDate from "./components/formatedDate.vue";
@Component({
  components: { FormatedDate }
})
export default class App extends Vue {}
</script>
