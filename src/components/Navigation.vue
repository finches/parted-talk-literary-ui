<!-- HTML -->
<template>
  <div id="navigation">
    <div class="overlay">
      <div class="questionwrapper">
        whats your name?
      </div>
    </div>
    <div class="content-panel">
      <div class="previous-lines">
        this text should take up the space on the top
      </div>
      <div class="writing-area">
        this should take up space below it
      </div>
    </div>
    <div class="user-panel">
      <user-panel v-bind:username="username"></user-panel>
    </div>
  </div>
</template>

<!-- Script -->
<script>
//child components
import UserPanel from "./User-Panel";

export default {
  name: 'navigation',
  components: {
    UserPanel
  },
  methods: {
    
  },
  data () {
    return {
      username: 'test name'
    }
  }
}
</script>

<!-- Styles -->
<style scoped>
  #navigation{
    width: 100%;
    height: 100%;
    display: flex;
    flex-direction: row;
  }

  .content-panel, .user-panel{
    height: 100%;
    display: inline-block;
    margin: 0;
  }

  .content-panel{
    flex-grow: .75;
  }

  .user-panel{
    flex-grow: .25;
  }

  .previous-lines{
    width: 100%;
    display: inline-block;
    background-color: aqua;
    height: 75%;
  }

  .writing-area{
    width: 100%;
    display: inline-block;
    background-color:lightcoral;
    height: 25%;
  }

  .overlay{
    position: absolute;
    left: 0;
    top: 0;
    width: 100vw;
    height: 100vh;
    background-color: white;
    display: flex;
    align-content: center;
    flex-direction: row;
    display: none;
  }
</style>
