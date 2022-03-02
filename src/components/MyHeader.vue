<template>
<nav class="navbar navbar-light bg-black">
  <div class="container-fluid">
    <h1 class="navbar-brand title">{{title}}</h1>
    <form class="d-flex" onSubmit="return false">
      <button @click="$emit('search', searchText)" class="btn" type="submit">
        <input v-model="searchText" class="form-control me-2" type="search" placeholder="Search" aria-label="Search">
      </button>
    </form>
  </div>
</nav>
</template>

<script>

    export default {
        name: "MyHeader",
        props: {
            "title": String
        },
        data() {
          return {
            searchText:''
          }
        }
    }

</script>

<style lang="scss" scoped>
.title{
    color: red;
}
</style>