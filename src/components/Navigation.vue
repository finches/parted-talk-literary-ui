<!-- HTML -->
<template>
  <div id="navigation">
    <div class="content-panel">
      <div class="previous-lines">
        this text should take up the space on the top
      </div>
      <div class="writing-area">
        this should take up space below it
      </div>
    </div>
    <div class="user-panel">
      this should be on the right
    </div>
  </div>
</template>

<!-- Script -->
<script>
export default {
  name: 'navigation',
  components: {
    
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
    flex-grow: .85;
  }

  .user-panel{
    background-color: thistle;
    flex-grow: .15;
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
