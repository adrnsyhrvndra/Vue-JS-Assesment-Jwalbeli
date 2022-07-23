<template>

  <div class="comment">

    <div class="comment__flex">

      <p>I found this article helpful</p>

      <div class="comment__flex-btn">

        <button type="button" class="btn btn-success update btn-lg">Update</button>

        <button type="button" class="btn btn-danger btn-lg del">Delete</button>

      </div>

    </div>

  </div>

</template>

<script>

  export default {

    name: 'CommentPost',

    methods: {

      sweetAlert() {

      this.$swal('Heading', 'this is a Heading', 'OK');

      }

    }

  }

</script>

<style>

  .message {

    margin-bottom: 2em;

  }

  .comment {
    
    margin: 1em 0 2em;

    border-bottom: 1px solid #ccc;

  }

  .comment__flex-btn {

    margin: 1em 0;

  }

  button + button {

    margin-left: 1em;

  }

  button {

    padding: 0.75em 1em;

    border: unset;

  }

  .del {

    background: #f93943;

    color: #000807;

  }

  .update {

    background: #7eb2dd;

    color: #000807;

  }

  textarea {

    width: 100%;

  }

  .open {

    margin: 1em 0;

  }

</style>