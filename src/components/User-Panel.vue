<!-- Template View -->
<template>
    <div id="userpanel">
        <div class="header">
            <h2>Users</h2>
        </div>
        <div class="userlist">
            <ul>
                <li id="currentuser">{{ username }}</li>
                <li>user 1</li>
                <li>user 2</li>
                <li>user 3</li>
            </ul>
        </div>
    </div>
</template>

<!-- Template Script -->
<script>
export default {
  name: 'user-panel',
  props: ['username'],
  components: {
    
  },
  methods: {
    
  },
  data () {
    return {

    }
  }
}
</script>

<!-- Styles -->
<style scoped>
#userpanel{
    box-sizing: border-box;
    border-left: 4px solid lightseagreen;
    height: 100%;
}

.header{
    text-align: center;
    padding: 1em 0;
    margin: 0 1em;
    border-bottom: 2px solid lightseagreen;
}

#currentuser{
    font-weight: 700;
}

h2{
    margin: 0;
}
</style>