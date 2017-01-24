<!-- HTML -->
<template>
    <div id="getname">
        <div id="content">
            <div id="question">what is your name?</div>
            <input type="text" v-model="name" v-on:keyup.enter="sendName()"/>
            <button type="button" v-on:click="sendName()">submit name</button>
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
    font-size: 4em;
}

#content{
    flex-grow: .6;
}
</style>