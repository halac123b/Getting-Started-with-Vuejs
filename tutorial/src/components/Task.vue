<template>
  <div class="task">
    <span>{{ taskData.content }}</span>
  </div>
</template>

<script>
export default {
  name: 'TaskData',
  props: {
    taskData: {
    type: Object,
    default: function() {return {}}
    }
  }
}
</script>