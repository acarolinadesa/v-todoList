<template>
  <div class="">
    <input v-model="text" type="text">
    <button @click="submit()">Cadastrar</button>
  </div>
</template>

<script>
  export default {
    data () {
      return {
        text: ''
      }
    },
    methods: {
      submit () {
        this.$emit('cadastrar', this.text)
        this.text = ''
      }
    }
  }
</script>