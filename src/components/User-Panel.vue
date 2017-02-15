<!-- Template View -->
<template>
    <div id="userpanel">
        <div class="header">
            <h2>Users</h2>
        </div>
        <div class="userlist">
            <ul>
                <li id="currentuser">{{ currentUser }}</li>
                <li v-for="id in connectedUsers">{{ users[id] }}</li>
            </ul>
        </div>
    </div>
</template>

<!-- Template Script -->
<script>
export default {
  name: 'user-panel',
  sockets:{
    // When a userName event is received, checks to see if its the current user
    // or if the name needs to be added to the greater list of users
    userName: function(val){
        if(val.id != this.userid){
            this.users[val.id] = val.name;
        }
        else{
            this.currentUser = val.name;
        }
        this.getUserIds();
    },
    // Sets up the initial list of connections
    initialUsers: function(val){
        val.forEach((returnedUser) => {
            if(returnedUser.id != this.userid) this.users[returnedUser.id] = returnedUser.name;
        });
        this.getUserIds();
    },
    // Removes a user when disconnecting
    removeUser: function(val){
        delete this.users[val];
        this.getUserIds();
    }
  },
  props: ['username', 'userid'],
  components: {
    
  },
  methods: {
    // Gets a list of user ids to render in the connected user box
    getUserIds: function(){
        var ids = [];
        for(var id in this.users) {
            if(id != this.userid && this.users[id] != "") ids.push(id);
        }
        this.connectedUsers = ids;
    }
  },
  data () {
    return {
        users: {},
        currentUser: '',
        connectedUsers: []
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