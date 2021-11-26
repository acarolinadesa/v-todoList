<template>
  <div class="">
    <div v-for="(task, index) of tasks" :key="index">
      <span v-if="editIndex !== index">{{ task }}</span>
      <input v-else v-model="text" type="text"/>

      <button @click="$emit('deleteById', index)">X</button>

      <button v-if="editIndex !== index" @click="edit(task, index)">Edit</button >
      <button v-else @click="submit(index)">Ok</button >
    </div>
  </div>
</template>

<script>
  export default {
    props: ['tasks'],
    data () {
      return {
        text: '',
        editIndex: null
      }
    },
    methods: {
      edit (task, index) {
        this.editIndex = index
        this.text = task
      },
      submit (index) {
        this.editIndex = null
        this.$emit('editById', {index, text: this.text})
        this.text = ''
      }
    }
}
</script>