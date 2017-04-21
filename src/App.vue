<template>
  <div id="app">
    <toolbar></toolbar>
    <notebox></notebox>
    <editor></editor>
  </div>
</template>

<script>
import editor from './components/Editor'
import notebox from './components/NoteBox'
import toolbar from './components/Toolbar'

export default {
  name: 'app',
  components: {
    editor,
    notebox,
    toolbar
  }
}
</script>

<style>
@import './common/css/reset.css';
#app {
  height: 100%;
  overflow: hidden;
}
body {
  border: 0;
  height: 100%;
  max-height: 100%;
  position: relative;
}
</style>
