<script>
import axios from 'axios';
import StudentLine from './StudentLine';
import AddStudent from './AddStudent';

export default {
  components: {
    StudentLine,
    AddStudent,
  },
  data() {
    return {
      students: [],
    };
  },
  methods: {
    getAll() {
      axios.get('http://localhost:3000/students')
      .then((response) => {
        this.students = response.data;
      });
    },
    remove(index) {
      axios.delete(`http://localhost:3000/students/${this.students[index].id}`)
      .then(() => {
        this.students.splice(index, 1);
      });
    },
    AddStudent(student) {
      axios.post('http://localhost:3000/students', student)
      .then((res) => {
        this.students.push(res.data);
      });
    },
  },
  mounted() {
    this.getAll();
  },
};
</script>

<template>
  <div>
    <student-line v-for='(student, index) in students' :student="student" v-on:remove="remove(index)"> </student-line>
    <AddStudent @create-student="AddStudent"></AddStudent>
  </div>
</template>

<style>
</style>
