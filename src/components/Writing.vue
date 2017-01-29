<!-- HTML -->
<template>
    <div id="writing">
        <div id="writing-title">
            <span>enter the {{ segmentName() }}:<span>
            <span id="charactersRemaining"> {{ 200 - content.length }} </span>
        </div>
        <div class="content-holder">
            <input type="text" v-model="content" v-on:keyup.enter="submitLine()" maxlength="200"/>
            <button type="button" v-on:click="submitLine()">►</button>
        </div>
    </div>
</template>

<!-- Script -->
<script>
export default {
  name: 'writing',
  props:['state'],
  components: {

  },
  methods: {
    submitLine: function(){
        if(this.state == 'sentence') this.content.endsWith('.') ? this.content += ' ' : this.content += '. ';
        this.$emit('content', this.content);
        this.$socket.emit('new-line', this.content);
        this.content = '';
    },
    segmentName: function(){
        if(this.state == 'title') return 'story title';
        else return 'next sentence'
    }
  },
  data () {
    return {
      content: ''
    }
  }
}
</script>

<!-- Styles -->
<style scoped>
    #writing{
        width: 100%;
        height: 100%;
        box-sizing: border-box;
        border-top: 4px solid lightseagreen;
        font-size: 1.5em;
        display: flex;
        flex-direction: column;
        align-items: left;
        justify-content: center;
        padding: 0 2em;
    }

    #writing-title{
        font-weight: 700;
    }

    input {
        border: none;
        border-bottom: 3px solid black;
        font-size: 1em;
        line-height: 16px;
        margin-right: 0;
        font-family: 'Avenir', Helvetica, Arial, sans-serif;
        outline: none;
        flex-grow: 1;
    }

    button{
        border:none;
        font-size: 0.81em;
        background-color:white;
        border-bottom: 3px solid black;
    }

    .content-holder{
        display: flex;
    }

    #charactersRemaining{
        float: right;
    }
</style>