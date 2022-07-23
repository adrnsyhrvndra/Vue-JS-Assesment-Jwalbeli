<template>

  <div class="container-fluid">

    <NavbarView />

    <div class="container-fluid">

      <div class="row">

        <div class="col-lg-12">

            <div class="jumbotron bg-white">

            <div class="container text-center">

              <h1 class="display-4">Home Page</h1>

              <p class="lead">This is a home page that include my identity.</p>

            </div>

          </div>

        </div>

      </div>

    </div>
    
    <div class="container">

      <div class="row">

        <div class="col-lg-12">

          <b-card img-src="https://i.ibb.co/MSWQ7Vh/image.jpg" img-alt="image" img-left class="mb-3" img-width="25%">

            <b-card-text>

              <div class="container">

                <div class="row">

                    <div class="col-lg-12">
                      
                      <span class="text-muted">My Name Is,</span>
                      
                      <h1>Adriansyah Ravindra</h1>

                      <h5>

                        Born In

                        <small class="text-muted">Jakarta 17 October 2002</small>

                      </h5>

                      <p class="lead" style="font-size:17px;">

                        So,i was born in jakarta 17 october 2002 , My last education is in Vocational High School choosing information technology major.But now i am in widyatama university choosing System Information Major.

                      </p>

                    </div>

                  </div>

              </div>

            </b-card-text>

          </b-card>

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

  </div>

</template>

<script>

  // @ is an alias to /src
  import NavbarView from '@/components/NavbarView.vue'

  export default {
    name: 'HomeView',
    components: {
      NavbarView
    }
  }
  
</script>