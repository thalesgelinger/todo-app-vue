<template>
  <li>
    <h3>{{ name }}</h3>
    <span class="material-icons" v-on:click="$emit('remove', id)">
      remove
    </span>
  </li>
</template>

<script>

export default {
  name: 'Task',
  props: {
    id: Number, 
    name: String
  }
}

</script>

<style scoped>
li {
  list-style: none;
  background: #35495E;
  color: #FFFFFF;
  width: 100%;
  min-width: 350px;
  padding-left: 10px;
  border-radius: 3px;
  margin-bottom: 10px;
  display: flex;
  justify-content:space-between;
}

li h3 {
  display: flex;
  align-items: center;
}

li > span {
  font-weight: bold;
  cursor: pointer;
  background: #41B883;
  padding: 5px 15px;
  border-radius: 0 3px 3px 0 ;
  transition: opacity .2s; 
}

span:hover {
  opacity: 0.4;
}
</style>