<template>
  <div id="formatedDate">
    <v-card  class="mx-auto my-12"
    max-width="800">
      <v-card-title >
        <span class="headline"
          >Date format day/month / year in Vuetify Vue Typescript
        </span>
      </v-card-title>
      <v-card-text>
        <v-row>
          <v-col cols="12" sm="6" md="4">
            <v-menu
              v-model="birthDateMenu"
              :close-on-content-click="false"
              :nudge-right="40"
              lazy
              transition="scale-transition"
              offset-y
              full-width
              max-width="290px"
              min-width="290px"
            >
              <template v-slot:activator="{ on }">
                <v-text-field
                  outlined
                  label="Birthdate"
                  v-on="on"
                  v-model="birthDate"
                ></v-text-field>
              </template>
              <v-date-picker v-model="currentDate">
                <v-spacer></v-spacer>
                <v-btn
                  color="primary"
                  @click="(birthDateMenu = false), getBirthdayDate('')"
                  >Cancel</v-btn
                >
                <v-btn
                  color="primary"
                  @click="(birthDateMenu = false), getBirthdayDate(currentDate)"
                  >OK</v-btn
                >
              </v-date-picker>
            </v-menu>
          </v-col>
        </v-row>
      </v-card-text>
    </v-card>
  </div>
</template>
<script lang="ts">
import { Vue, Component } from "vue-property-decorator";
@Component({
  components: {}
})
export default class FormatedDate extends Vue {
  //Variable declaration
  private birthDateMenu = false;
  private birthDate = "";
  private date: any = "";
  private currentDate: any = new Date().toISOString().substr(0, 10);

  //Format Date for display
  formatDate(date: any) {
    if (!date) return null;
    const [year, month, day] = date.split("-");
    return `${day}/${month}/${year}`;
  }

  //format date for picker to understand format
  formatPickerDate(date: any) {
    if (!date) return null;
    const [day, month, year] = date.split("/");
    return `${year}-${month}-${day}`;
  }

  get computedBirthDate() {
    let result = this.date;
    if (this.birthDate !== null) {
      result = this.birthDate;
    }
    if (result.indexOf("-") !== -1) {
      result = this.formatDate(result);
    }
    return result;
  }

  set computedBirthDate(date: string) {
    this.birthDate = date;
  }

  //Computed Method to get date and clear date if not picked
  getBirthdayDate(value: any) {
    if (value !== "") {
      this.birthDate = value;
      this.birthDate = this.computedBirthDate;
    } else {
      this.birthDate = "";
    }
  }
}
</script>
