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
    userName: function(val){
        if(val.id != this.userid){
            this.users[val.id] = val.name;
        }
        else{
            this.currentUser = val.name;
        }
        this.getUserIds();
    },
    initialUsers: function(val){
        val.forEach((returnedUser) => {
            if(returnedUser.id != this.userid) this.users[returnedUser.id] = returnedUser.name;
        });
        this.getUserIds();
    },
    removeUser: function(val){
        delete this.users[val];
        this.getUserIds();
    }
  },
  props: ['username', 'userid'],
  components: {
    
  },
  methods: {
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