<template>
<div>
      <h1>Instructions</h1>
      <ul>
        <li>Click on the button and press enter or space to toggle visibility of dropdown </li>
        <li>Use up and down arrow key to choose an option</li>
        <li>Click Enter to choose that option</li>
        <li>Press esc to exit dropdown</li>
       </ul>
      <HelloWorld/>
</div>

</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
