<template>

  <div class="home container">

    <NavbarView />

      <div class="container-fluid">

      <div class="row">

        <div class="col-lg-12">

            <div class="jumbotron bg-white">

            <div class="container text-center">

              <h1 class="display-4">Comment Page</h1>

              <p class="lead">This is a comment page for the comment form.</p>

            </div>

          </div>

        </div>

      </div>

    </div>

      <div class="container">

        <div class="row">
          
          <div class="col-lg-12">
            
            <div class="form">

              <div class="comment-space">

                  <h4>Comment Form</h4>

                  <div class="comment">

                    <div class="comment__flex">

                      <ul v-for="commen in comment" :key="commen.id" class="list-group">

                        <li class="list-group-item my-1">

                          <span>{{commen.komentar}}</span> &#160;

                        </li>

                        <li class="list-group-item my-1">

                          <div class="comment__flex-btn">

                            <b-button v-b-modal.modal-1 type="button" class="btn btn-success update btn-sm mt-3" @click="edit(commen)">Update</b-button>

                            <button type="button" class="btn btn-danger btn-sm del mt-3" @click="del(commen)">Delete</button>

                          </div>

                        </li>

                      </ul>

                    </div>

                  </div>

              </div>

              <form @submit.prevent="add">

                <div class="form__group">

                  <label>Leave a comment</label>

                    <input type="hidden" v-model="form.id">

                    <textarea class="form-control" id="exampleFormControlTextarea1" cols="50" rows="10" v-model="form.komentar" placeholder="type the body of your comment"></textarea>

                    <button type="submit" class="btn btn-success btn-lg mt-3" v-show="!updateSubmit">Submit</button>

                    <button type="button" class="btn btn-success btn-lg mt-3" v-show="updateSubmit" @click="update(form)">Update</button>

                </div>

              </form>

            </div>

          </div>
          
        </div>

      </div>

      <div class="container">

      <footer class="d-flex flex-wrap justify-content-between align-items-center py-3 my-4 border-top">

        <div class="col-md-4 d-flex align-items-center">

          <a href="/" class="mb-3 me-2 mb-md-0 text-muted text-decoration-none lh-1">

            <b-icon icon="shop-window" class="rounded bg-warning p-1" variant="dark"></b-icon>

          </a>

          <span class="text-muted ml-1"> &copy; 2022 Jwalbeli Company</span>

        </div>

      </footer>
      
    </div>

    <!-- Modal -->

    <b-modal id="modal-1" title="Edit Your Comment" hide-footer v-show="updateSubmit" v-if="showModal">
      
      <input type="hidden" v-model="form.id">

      <textarea class="form-control" id="exampleFormControlTextarea1" cols="50" rows="10" v-model="form.komentar" placeholder="type the body of your comment"></textarea>

      <button type="submit" class="btn btn-success btn-sm mt-3" v-show="updateSubmit" @click="update(form)">Update</button>

    </b-modal>

  </div>

</template>

<script>

  /* eslint-disable */ 

  import axios from 'axios';

  import NavbarView from '@/components/NavbarView.vue';

  export default {

    name: 'CommentView',

    components: {

      NavbarView

    },
    data(){
      return{
          form: {
            id: '',
            komentar: ''
          },
          comment: '',
          showModal: false,
          updateSubmit: false
      }
    },
    mounted() {
      this.load()
    },
    methods: {
      load(){
          axios.get('http://localhost:3000/comment').then(res => {
          this.comment = res.data
        }).catch ((err) => {
          console.log(err);
          
        })
      },
      add(){
        axios.post('http://localhost:3000/comment/', this.form).then(res => {
            this.load()
            this.form.komentar = ''
            this.$swal('Berhasil!', 'Data Berhasil Ditambahkan', 'OK');
        })
      },
      edit(commen){ 
          this.updateSubmit = true
          this.form.id = commen.id 
          this.form.komentar = commen.komentar
          this.showModal = true
      },
      update(form){ 
        return axios.put('http://localhost:3000/comment/' + form.id , {komentar: this.form.komentar}).then(res => {
          this.load()
          this.form.id = '' 
          this.form.komentar = ''
          this.updateSubmit = false
          this.showModal = false
        }).catch((err) => {
          console.log(err);
          
        })
      },
      del(commen){

        this.$swal({
        title: 'Are you sure?',
        text: 'You can\'t revert your action',
        type: 'warning',
        showCancelButton: true,
        confirmButtonText: 'Yes Delete it!',
        showCloseButton: true,
        showLoaderOnConfirm: true
      }).then((result) => {
        if(result.value) {
          axios.delete('http://localhost:3000/comment/' + commen.id).then(res =>{
          this.load()
          let index = this.comment.indexOf(form.komentar)
          this.comment.splice(index,1)
          this.$swal('Deleted', 'You successfully deleted this file', 'success')
      })} else {
          this.$swal('Cancelled', 'Your file is still intact', 'info')
        }
      })


      }
    }
  }

</script>