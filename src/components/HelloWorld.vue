<template>
  <v-container>
   <v-form
    ref="form"
    lazy-validation
  >
    <v-text-field
      v-model="internalValue"
      label="Name"
      required
      
    ></v-text-field>

    
  </v-form>
  </v-container>
</template>

<script>
  export default {
    name: 'HelloWorld',

    props:{
      value: null
    },
    watch: {
    internalValue(value) {
        this.$emit('value-updated', value); //emit event to parent
    }
    },
    data: () => ({
      internalValue: null 
    }),
    mounted() {
      this.internalValue = this.value
    }
  }
</script>
