<template>
  <div class="">
    <div v-for="(task, index) of tasks" :key="index">
      <span v-if="whoIsEditing !== index">
        {{ task.title }}
      </span>
      <input v-else v-model="text" type="text"/>

      <button @click="$emit('deleteById', index)">X</button>

      <button v-if="whoIsEditing !== index" @click="edit(task, index)">Edit</button >
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
        whoIsEditing: null
      }
    },
    methods: {
      edit (task, index) {
        this.whoIsEditing = index
        this.text = task.title
      },
      submit (index) {
        this.whoIsEditing = null
        this.$emit('editById', {index, text: this.text})
        this.text = ''
      }
    }
}
</script>