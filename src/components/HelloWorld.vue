<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
  </div>
</template>

<script>
function func1(num){
    return new Array((num * 1024) + 1).join('a')
}

// Determine the size of localStorage if it's not set

if (!localStorage.getItem('size')) {
var i = 0;
try {
    // Test up to 10 MB
    for (i = 0; i <= 10000; i += 250) {
        localStorage.setItem('test', func1(i));
    }
    } catch (e) {
    localStorage.removeItem('test');
    localStorage.setItem('size', i ? i - 250 : 0);
    }
}
          
// when window is loaded this function is
// called and the size of localStorage is calculated    
window.onload = function calculate(){
    var el = document.getElementById('size');        
    el.innerHTML = localStorage.getItem('size');
}
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  h3 {
    margin: 40px 0 0;
  }
  ul {
    list-style-type: none;
    padding: 0;
  }
  li {
    display: inline-block;
    margin: 0 10px;
  }
  a {
    color: #42b983;
  }
</style>
