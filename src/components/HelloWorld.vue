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
      //prop passed from parent's v-model
      value: null
    },
    watch: {
    //watching the internalValue data property  
    internalValue(value) {
        this.$emit('value-updated', value); //emit event to parent
    }
    },
    data: () => ({
      internalValue: null //data binding with v-model on this property. 
    }),
    mounted() {
      //Initially set for vieweing
      this.internalValue = this.value
    }
  }
</script>
