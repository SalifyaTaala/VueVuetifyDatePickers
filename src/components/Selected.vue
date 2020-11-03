<template>
  <div id="SelectItem">
    <v-row>
      <v-col cols="12" md="6">
        <v-select
          :items="items"
          label="Standard"
          @change="selectedButton"
          v-model="selected"
          dense
        >
        </v-select>
      </v-col>
    </v-row>
    <div v-if="selected === 'Red Button'">
      <v-col cols="12" md="4">
        <v-btn small color="error">Red button</v-btn>
      </v-col>
    </div>
    <div v-if="selected === 'Green Button'">
      <v-col cols="12" md="4">
        <v-btn small color="success">Green button</v-btn>
      </v-col>
    </div>
  </div>
</template>

<script lang="ts">
import { Vue, Component } from "vue-property-decorator";

@Component({
  components: {}
})
export default class SelectItem extends Vue {
  items: Array<string> = ["Red Button", "Green Button"];

  //the selected variable is declared to reset the v-select options
  private selected = "";
  //method
  selectedButton() {
    console.log("test");
  }
}
</script>
