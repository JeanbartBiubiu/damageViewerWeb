<template>
    <div>
      <select v-model="selectedOption">
        <option v-for="option in options" :key="option.gameCode" :value="option.gameName">
          {{ option.gameName }}
        </option>
      </select>
      <button @click="navigate">Go</button>
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  
  export default {
    data() {
      return {
        options: [],
        selectedOption: ''
      };
    },
    created() {
      this.fetchOptions();
    },
    methods: {
      fetchOptions() {
        axios.get('http://127.0.0.1:8888/test/gameInfo')
          .then(response => {
            this.options = response.data;
          })
          .catch(error => {
            console.error('There was an error fetching the options!', error);
          });
      },
      navigate() {
        if (this.selectedOption) {
          this.$router.push(this.selectedOption);
        } else {
          alert('Please select an option first!');
        }
      }
    }
  };
  </script>
  
  <style scoped>
  /* 你可以在这里添加样式 */
  </style>
  