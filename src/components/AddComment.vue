<template>

  <div class="form">

    <form>

      <div class="form__group">

        <label>Leave a comment</label>

          <textarea class="form-control" id="exampleFormControlTextarea1" cols="50" rows="10" v-model="newComment" placeholder="type in your comment"></textarea>

          <button type="button" class="btn btn-success btn-lg">Submit</button>

      </div>

    </form>

  </div>

</template>

<script>

  export default {

    name : 'AddComment',

    data() {

      return {

        newComment: '',
        
      };

    },

  };

</script>

<style scoped>

  .form {

    margin-top: 1.5em;

  }

  label {

    display: block;

    margin-bottom: 1em;

    font-weight: 700;

    font-family: Padauk, sans-serif;

  }

  textarea {

    width: 100%;
    margin-top: 0.5em;

  }

  button {

    border: unset;

    background: #79b791;

    color: #230c0f;

    font-weight: 700;

    padding: 1em 2.5em;

    margin-top: 1em;
    
  }

</style>