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
  },
  methods: {
    show() {
    }
  }
}
</script>

<style lang="scss">

$input-width: 180px;
$input-padding: 5px 5px;
$input-height: 15px;

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
}

.create {
  margin: auto;
  background-color: #ffffff;
  padding: 30px;
}

.btn {
  width: 150px;
  margin: 0 30px 30px;
  padding: 10px;
  cursor: pointer;
}

.form {
  display: flex;
  flex-wrap: wrap;
  &-block {
    padding: 30px;
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

      &_textarea {
        width: $input-width+2;
        padding: $input-padding;
        height: 100px;
        resize: none;
      }

      &_select {
        width: $input-width+14;
        padding: $input-padding;
        -ms-overflow-style: none; 
        &::-webkit-scrollbar { width: 0; }
      }
    }
  }
}
</style>
