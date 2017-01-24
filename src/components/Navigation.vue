<!-- HTML -->
<template>
  <div id="navigation">
    <get-name v-on:username="setUsername($event)"></get-name>
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
import GetName from "./Get-Name";

export default {
  name: 'navigation',
  components: {
    UserPanel,
    GetName
  },
  methods: {
    setUsername(name){
      this.username = name;
    }
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
</style>
