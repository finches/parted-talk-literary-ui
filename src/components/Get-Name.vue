<!-- HTML -->
<template>
    <div id="getname">
        <div id="content">
            <div id="question">what is your name?</div>
            <div class="question-holder">
                <input type="text" v-model="name" v-on:keyup.enter="sendName()" maxlength="16"/>
                <button type="button" v-on:click="sendName()">►</button>
            </div>
        </div>
    </div>
</template>

<!-- Script -->
<script>
export default {
  name: 'get-name',
  components: {
    
  },
  methods: {
    sendName() {
        this.$el.style.display = 'none';
        this.$emit('username', this.name);
    }
  },
  data () {
    return {
      name: ''
    }
  }
}
</script>

<!-- Styling -->
<style scoped>
#getname{
    position: absolute;
    background-color: white;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    font-size: 2.827em;
}

#content{
    flex-grow: .6;
}

input {
    border: none;
    border-bottom: 3px solid black;
    font-size: 1em;
    line-height: 16px;
    margin-right: 0;
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    outline: none;
}

button{
    border:none;
    font-size: 0.81em;
    background-color:white;
    position:absolute;
    right: 0;
    top: 8px;
}

.question-holder{
    position:relative;
}
</style>