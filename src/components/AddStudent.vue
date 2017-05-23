<script>
  export default {
    data() {
      return {
        newStudent: {
          firstname: '',
          name: '',
          age: '',
        },
      };
    },
    methods: {
      add() {
        const student = this.newStudent;
        this.$emit('create-student', student);
      },
    },
  };
</script>

<template>
  <form class="form">
  <input v-model='newStudent.firstname' placeholder="First name"></input>
  <input v-model='newStudent.name' placeholder="Name"></input>
  <input v-model='newStudent.age' placeholder="Age"></input>
  <button @click="add"> Ajouter </button>
  </form>
</template>

<style>
.form {
  margin-top: 50px;
}
</style>
