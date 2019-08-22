<template>
    <div class="search-wrapper">
      <input id="search" name="search" v-model="searchValue" @input="eventHandler" />
    </div>
</template>


<script>
export default {
    name: "SearchInput"
}
</script>

<style lang="scss" scoped>
.search-wrapper {
  display: flex;
  flex-direction: column;
  width: 300px;

  input {
      margin-top: 50px;
    height: 30px;
    border: 0;
    background: none;
    border-bottom: 1px solid black;
  }
}
</style>