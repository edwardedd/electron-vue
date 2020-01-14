<template>
<form @submit.prevent ="submitForm">

    <div class="form-group">
        <h1>The User Page</h1>
        <hr>
        <input  v-model="value"
        type="number"
        min="0"
        max="10"
        required/>
        <button
        class="btn btn-success"
        >Save</button>
    </div>
</form>
</template>

<script>
export default {
  name: 'User',
  data() {
    return {
      form:{
        value: null
      }
    }
  },
  mounted() {
    if (localStorage.value) {
      this.value = localStorage.value;
    }
  },
  methods: {
    submitForm(){
      window.console.log(this.form)
      this.changeInputValue()
    },
    changeInputValue(){
      localStorage.value = this.$store.state.value;
    }
  },
  computed: {
    value:{
      get(){
        return this.$store.state.value
      },
      set(value){
        this.$store.commit('updateValue', value)
      }
    }
  }
}
</script>