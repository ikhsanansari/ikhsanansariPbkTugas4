<template>
    <div>
      <input type="number" v-model="userGuess" placeholder="Masukkan tebakan Anda" />
      <button @click="emitCheckGuess">Cek Tebakan</button>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        userGuess: null
      };
    },
    methods: {
      emitCheckGuess() {
        this.$emit('checkGuess', this.userGuess);
      }
    }
  };
  </script>
  
  <style>
  input[type='number'] {
    width: 100px;
    margin-bottom: 10px;
  }
  button {
    padding: 10px 20px;
    cursor: pointer;
  }
  </style>
  