<template>
  <div id="app">
    <h1>Better Links/Nav</h1>

    <p>Links with no extra visual indication of hover/focus state have issues knowing which is correct one to click</p>

    <h2>Big problem if there are only 2 options</h2>
    <p>Is one of these already highlighted (defaulted)?  Which one?</p>
    <ul>
      <li><a href="#">Submit</a></li>
      <li><a href="#" class="cancel">Cancel</a></li>
    </ul>
    <h2>This is less of an issue if there are multiple options</h2>
    <ul>
      <li><a href="#">test 1</a></li>
      <li><a href="#">test 2</a></li>
      <li><a href="#">test 3</a></li>
      <li><a href="#">test 4</a></li>
      <li><a href="#">test 5</a></li>
    </ul>

    <hr>
    <h2>A better way has extra graphical treatment</h2>
    <ul class="better-hilites">
      <li><a href="#">Submit</a></li>
      <li><a href="#" class="cancel">Cancel</a></li>
    </ul>
    <h2>Seen with multiple options</h2>

    <ul class="better-hilites">
      <li><a href="#">test 1</a></li>
      <li><a href="#">test 2</a></li>
      <li><a href="#">test 3</a></li>
      <li><a href="#">test 4</a></li>
      <li><a href="#">test 5</a></li>
    </ul>

  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      msg: ''
    }
  }
}
</script>

<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
p {
  font-size: 1.1em;
}
h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
  margin: 30px;
  li {
    display: inline-block;
    margin: 0;
  }
}


li {
  a {
    display: block;
    padding: 20px;
    background: black;
    color: white;
    position: relative;
    overflow: hidden;
    transition: all 0.3s;
    text-decoration: none;
    border: 1px solid black;
    &:hover, &:focus {
      background: white;
      color: black;
      text-decoration: underline;
    }
    &.cancel {
      border: 1px solid black;
      background: white;
      color: black;
      &:hover,
      &:focus {
        background: black;
        color: white;
      }
    }
  }
}
.better-hilites a {
  transition: none;
  border: 1px solid black;

  &:before, &:after {
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
    width: 2px;
    height: 100%;
    border-radius: 6px;
    font-size: 4em;
    line-height: 1;
    content: "";
    left: -10px;
    right: 5px;
    transition: left 0.3s, right 0.3s;
  }

  &.cancel {
    &:hover,
    &:focus {
      background: white;
      color: black;
    }
  }

  &:hover, &:focus {
    background: white;
    color: black;
    text-decoration: none;
    border: 1px solid transparent;

    &::before{
      content: "[";
      left: -4px;
      right: auto;
    }
    &::after{
      content: "]";
      right: 11px;
      left: auto;
    }
  }
}
</style>
