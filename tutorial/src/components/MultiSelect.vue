<template>
  <div>
    <div class="list">
      <div 
        v-for="(language, index) in languages" 
        :key="index"
        @click="language.selected=!language.selected"
        :class={selected:language.selected}>
        <span>{{ language.name }}</span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'MultiSelect',
  data() {
    return {
      languages: [
        { name: 'PHP', selected: false },
        { name: 'JavaScript', selected: false },
        { name: 'Cpp', selected: false },
        { name: 'Python', selected: false }
      ]
    }
  }
}
</script>

<style>
  .list div {
    display: inline-block;
    border: 1px solid black;
    padding: 4px 15px;
    margin-right: 5px;
    border-radius: 4px;
  }
  .selected {
    background-color: green;
    color: white;
  }
</style>