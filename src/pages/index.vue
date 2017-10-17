<template>
  <ul>
    <li v-for="fact in facts" :key="fact.text">
      {{ fact.text }}
    </li>
  </ul>
</template>

<script>
import fetch from 'isomorphic-fetch';

export default {
  async asyncData () {
    let response = await fetch('https://nuxt-ssr.firebaseio.com/facts.json');
    let facts = await response.json();
    return { facts }
  }
}
</script>

<style>
body {
  background-color: #c6e0f8;
  font-family: Roboto, Arial, sans-serif;
  max-width: 960px;
  margin: 0 auto;
  padding: 0 40px
}
ul {
  padding: 0;
  margin: 0
}
ul li {
  font-size: 18px;
  list-style-type: none;
  height: 48px;
  width: 100%;
  color: rgba(0, 0, 0, .63);
  border-bottom: 1px dashed rgba(0, 0, 0, .42);
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-align: center;
  -ms-flex-align: center;
  align-items: center
}
</style>
