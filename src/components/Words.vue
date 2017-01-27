<!-- HTML -->
<template>
    <div id="words">
        <div id="title">{{ title }}</div>
        <div v-for="paragraph in formatContent()" class="paragraph">{{ paragraph }}</div>
    </div>
</template>

<!-- Script -->
<script>
export default {
  name: 'words',
  props:['content', 'title'],
  components: {

  },
  methods: {
    formatContent: function(){
        return this.content.split("[br]").filter((v) => { return v.length > 0; });
    }
  },
  data () {
    return {

    }
  }
}
</script>

<!-- Styles -->
<style scoped>
#words{
    text-align: center;
    font-family: Cambria, Cochin, Georgia, Times, Times New Roman, serif;
    padding: 1em 5em;
    overflow: scroll;
    margin: 0;
    height: 100%;
    box-sizing: border-box;
    border: none;
    margin-bottom: -4px;
}

#title{
    font-size: 2.2827em;
    font-weight: 500;
}

.paragraph{
    font-size: 1.2em;
    line-height: 1.5em;
    margin-bottom: 1em;
    text-align: left;
}
</style>