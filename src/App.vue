<template>
  <div id="app">
    <ClientForm />
  </div>
</template>

<script>

import ClientForm from './components/clients'

export default {
  name: 'App',
  components: {
    ClientForm
  }
}
</script>

<style lang="scss">

$input-width: 180px;
$input-padding: 5px 10px;
$input-height: 15px;

%border {
  margin-bottom: 5px;
  background-color: #fbfbfb;
  border: 1px solid #ddd;
    &:hover, &:focus, &:active  {
      border: 1px solid #000000;
      outline: none;
    }
}

* {
  margin: 0;
  padding: 0;
}

body {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 10vh 0;
  background-color: #e2e2ee;
  font-family: Arial, Helvetica, sans-serif;
}

p {
  font-size: 12px;
  color: #666
}

.create {
  margin: auto;
  background-color: #ffffff;
  padding: 0px 30px;
}

.btn {
  width: 150px;
  margin: 0 30px 20px;
  padding: 10px;
  cursor: pointer;
}

.error {
  border-color: red !important;
  outline: none;
  outline-offset: 0;
  &:active, :focus {
    outline: none;
    outline-offset: 0;
  }
}

.form {
  display: flex;
  flex-wrap: wrap;
  &-block {
    padding: 15px 30px 5px;
  }

  &-group {
    margin-bottom: 15px;
    &__label {
      display: block;
      margin-bottom: 10px;
      
      &_radio {
        margin-left: 5px;
        margin-right: 10px;
      }

      &_checkbox {
        margin-left: 5px;
      }
    }

    &__input {
      width: $input-width;
      height: $input-height;
      padding: $input-padding;
      @extend %border;

      &_textarea {
        width: $input-width+2;
        padding: $input-padding;
        height: 100px;
        resize: none;
        @extend %border;
      }

      &_select {
        width: $input-width+20;
        padding: $input-padding;
        -ms-overflow-style: none; 
        &::-webkit-scrollbar { width: 0; }
        @extend %border;
      }
    }
  }
}
</style>
