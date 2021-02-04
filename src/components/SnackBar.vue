<template>
  <v-snackbar v-model="show" :top="top" :color="color">
    {{message}}
    <v-btn flat color="accent" @click.native="show = false">
      <v-icon>close</v-icon>
    </v-btn>
  </v-snackbar>
</template>

<script>
  export default {
    data() {
      return {
        show: true,
        top: true,
        message: "asd",
        color: "red",
        timeout: 5000
      };
    },
    created: function() {
      /*this.$store.watch(
        state => state.snackbar.snack,
        () => {
          const message = this.$store.state.snackbar.snack.message;
          if (message) {
            this.show = true;
            this.message = message;

            this.color = this.$store.state.snackbar.snack.color;
            this.$store.commit("snackbar/setSnack", {});
          }
        }
      );*/
    }
  };
</script>