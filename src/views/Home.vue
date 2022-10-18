<template>
  <div class="home">
    <todo-first-page />
  </div>
</template>

<script>
// @ is an alias to /src
import TodoFirstPage from '../components/TodoFirstPage.vue'
export default {
  name: 'Home',
  components: {
    TodoFirstPage
  }
}
</script>
