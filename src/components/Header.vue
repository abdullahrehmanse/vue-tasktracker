<template>
  <header>
    <h1>{{title}}</h1>
    <!--    <h1>Task Tracker</h1>-->
    <Button text="Add Task" color="green" />
<!--    <Button text="Update Task" color="blue" />-->
<!--    <Button text="Delete Task" color="red" />-->
  </header>
</template>

<script>
import Button from "@/components/Button";
export default {
  name: 'Header',
  components: {Button},
  props: {
    title: {
      type: String,
      default: 'Hello World'
    }
  }
}
</script>

<style scoped>
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
}
</style>
