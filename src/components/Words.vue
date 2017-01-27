<!-- HTML -->
<template>
    <div id="words">
        <div id="title">{{ title }}</div>
        <div v-for="paragraph in formatContent()" class="paragraph">{{ paragraph }}</div>
    </div>
</template>

<!-- Script -->
<script>
var fakeContent = '';
for(var i = 0; i < 50; i++){
    fakeContent += "this is placeholder text meant to take up space. there should be around 5 sentences per paragraph. it should be centered on the page with an appropriate amount of margin. there could be a up to 1000 characters per paragraph but thats fine. there might be a good way to split up the string"
                + "[br]";
}

export default {
  name: 'words',
  components: {

  },
  methods: {
    formatContent: function(){
        return this.content.split("[br]").filter((v) => { return v.length > 0; });
    }
  },
  data () {
    return {
        title: "An Example Title",
        content: fakeContent,
        paragraph: ''
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