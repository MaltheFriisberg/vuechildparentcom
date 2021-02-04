<template>
  <v-app>
    <Snackbar />
    <v-app-bar
      app
      color="primary"
      dark
    >
      <div class="d-flex align-center">
        <v-img
          alt="Vuetify Logo"
          class="shrink mr-2"
          contain
          src="https://cdn.vuetifyjs.com/images/logos/vuetify-logo-dark.png"
          transition="scale-transition"
          width="40"
        />

        <v-img
          alt="Vuetify Name"
          class="shrink mt-1 hidden-sm-and-down"
          contain
          min-width="100"
          src="https://cdn.vuetifyjs.com/images/logos/vuetify-name-dark.png"
          width="100"
        />
      </div>

      <v-spacer></v-spacer>

      <v-btn
        href="https://github.com/vuetifyjs/vuetify/releases/latest"
        target="_blank"
        text
      >
        <span class="mr-2">Latest Release</span>
        <v-icon>mdi-open-in-new</v-icon>
      </v-btn>
    </v-app-bar>

    <v-main>
      <HelloWorld v-model="greeting" v-on:value-updated="greeting=$event"/>
      <v-date-picker
        :min="getMinStartDate"
        v-model="startDate"
      >


      </v-date-picker>
      <v-date-picker
        :min="getMinEndDate"
      >


      </v-date-picker>

      <v-container>
        <v-row align="center">
            <v-card
      max-width="600px"
      class="justify-center"
      align="center"
      justify="center"
      >

        <v-form>
          <v-container>
            <v-row>
              <v-col
                cols="12"
                md="12"
              >
              <v-text-field
                v-model="firstname"
                :rules="nameRules"
                :counter="10"
                label="First name"
                required
              ></v-text-field>
            </v-col>

            <v-col
              cols="12"
              md="12"
            >
              <v-btn
                
              >RESET</v-btn>
            </v-col>

            
      </v-row>


          </v-container>

        </v-form>

      </v-card>
        </v-row>
    </v-container>


      
    </v-main>
  </v-app>
</template>

<script>
import HelloWorld from './components/HelloWorld';
import Snackbar from "./components/SnackBar";
Date.prototype.addDays = function(days) {
    var date = new Date(this.valueOf());
    date.setDate(date.getDate() + days);
    return date;
}

Object.defineProperty(Date.prototype, "toISODateString", {
    value: function toISODateString(date) {
        return date.toISOString().substring(0, 10);
    },
    writable: true,
    configurable: true
});
export default {
  name: 'App',

  components: {
    HelloWorld,
    Snackbar
  },

  computed:{
    getMinStartDate() {
      var today = new Date();
      return today.toISOString().substring(0, 10);

    },
    getMinEndDate() {
      //var today = new Date(this.startDate);
      //console.log(today.addDays(10));
      
      return this.startDate ? new Date(this.startDate).addDays(10).toISOString().substring(0, 10) : new Date().toISOString().substring(0, 10);

    }
  },

  data: () => ({
    startDate: null,
    greeting : "mutate me, go ahead"
  }),
  mounted() {
    var today = new Date();
    var date = today.toISOString().substring(0, 10);
    console.log(today);
    console.log(date);
  }
};

</script>
