<!-- HTML -->
<template>
  <div id="navigation">
    <get-name v-on:username="setUsername($event)"></get-name>
    <div class="content-panel">
      <div class="previous-lines">
        <words v-bind:content="content" v-bind:title="title"></words>
      </div>
      <div class="writing-area">
        <writing v-bind:state="getState()" v-on:content="submitContent($event)"></writing>
      </div>
    </div>
    <div class="user-panel">
      <user-panel v-bind:username="username" v-bind:userid="userId"></user-panel>
    </div>
  </div>
</template>

<!-- Script -->
<script>
//child components
import UserPanel from "./User-Panel";
import GetName from "./Get-Name";
import Writing from "./Writing";
import Words from "./Words";

export default {
  name: 'navigation',
  components: {
    UserPanel,
    GetName,
    Writing,
    Words
  },
  sockets:{
    // Gets the initial set of messages and passes it to the primary render component
    initialMessages: function(val){
      val.forEach((m) => {
        this.submitContent(m);
      });
    },
    // Gets the current user's ID
    connId: function(val){
      this.userId = val;
    },
    // Adds a new message to the list
    newMessage: function(val){
      this.submitContent(val);
    },
    // Clears the list of messages when the maximum is reached
    clearScreen: function(val){
      this.content = '';
      this.title = '';
    }
  },
  methods: {
    // Sets the current user's name
    setUsername: function(name){
      this.username = name;
    },
    // Submits content to the correct child component in a format it's epxecting
    submitContent: function(content){
      if(this.getState() == 'title') this.title = content;
      else{
        this.content += content;
        if(Math.random() > 0.85) this.content += "[br]";
      }
    },
    // Determines if a title or sentence should be submitted
    getState: function(){
      if(this.title.length == 0) return 'title';
      else return 'sentence';
    }
  },
  data () {
    return {
      username: 'test name',
      content: '',
      title: '',
      userId: ''
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
    width: 75%;
  }

  .user-panel{
    width: 25%;
  }

  .previous-lines{
    width: 100%;
    display: inline-block;
    height: 75%;
  }

  .writing-area{
    width: 100%;
    display: inline-block;
    height: 25%;
  }
</style>
