<template>

  <div class="card" style="width: 17rem;">

    <div class="card-body">

      <h5 class="card-title">{{ post.title }}</h5>

      <p class="card-text">{{ post.body }}</p>

    </div>

    <ul class="list-group list-group-flush">

      <li class="list-group-item">ID : {{ post.id }}</li>

      <li class="list-group-item">USER ID :{{ post.userId }}</li>

    </ul>

  </div>    

</template>

<script>
export default {
    name : 'CardPost',
    props : ['post']
};
</script>

<style>

</style>