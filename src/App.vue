// Detta är en html template, man kan säga att det är html för att göra det lätt
// Varje component måste ha en template tag
<template>
  <div id="wrapper">
    <h1>{{title}}</h1>
    <p id="desc">{{desc}}</p>

    <input type="text" ref="name"/>
    <button @click="handleClick">Click Me</button>
</div>
</template>

<script>

//Det här är 'root object/component', den har data, methods osv.
export default {
  name: 'App',
  data() {
    return {
      title: 'My First Vue App',
      desc: 'Learning Vue :)'
    }
  },
  //Methods sköter metoder/functioner i våra components
  methods: {
    handleClick() {
      //För att komma åt input
      console.log(this.$refs.name)
      this.$refs.name.classList.add('active')
      this.$refs.name.focus()
    }
  } 
}
</script>

/* Här är style, precis som css */
<style>
#wrapper {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  box-sizing: border-box;
}

#wrapper > h1{
  border-bottom: 2px solid #ddd;
  padding-bottom: 10px;
}

#desc{
  font-size: 1.5rem;
}
</style>
