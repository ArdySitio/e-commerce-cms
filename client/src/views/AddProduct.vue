<template>
<div>
   <Navbar />
  <div class="container">
       <div class="row">
        <div class="col-sm-9 col-md-7 col-lg-5 mx-auto">
            <div class="card card-signin my-5">
            <div class="card-body">
                <h3 class="card-title text-center text-dark">New Product</h3>
                <form @submit.prevent="submitAddProduct" class="form-addProduct">

                    <div class="form-label-group">
                        <label for="name">Product Name</label>
                        <input type="text" v-model="name" class="form-control" required>
                    </div>
                    <div class="form-label-group">
                        <label for="image_url">Image Url</label>
                        <input type="text" v-model="image_url" class="form-control">
                    </div>
                    <div class="form-label-group">
                        <label for="price">Price</label>
                        <input type="text" v-model="price" class="form-control" required>
                    </div>
                    <div class="form-label-group">
                        <label for="stock">Stock</label>
                        <input type="text" v-model="stock" class="form-control" required>
                    </div><br>

                    <button class="btn btn-lg btn-primary btn-block text-uppercase" type="submit">Add Prooduct</button>
                </form>
            </div>
            </div>
        </div>
        </div>
  </div>
</div>
</template>

<script>
import Navbar from '../components/Navbar'
export default {
  name: 'AddProduct',
  data () {
    return {
      name: '',
      image_url: '',
      price: '',
      stock: ''
    }
  },
  components: {
    Navbar
  },
  methods: {
    submitAddProduct () {
      this.$store.dispatch('addProduct', {
        name: this.name,
        image_url: this.image_url,
        price: this.price,
        stock: this.stock
      })
        .then((data) => {
          this.$router.push('/')
        })
    }
  }
}
</script>

<style>

</style>
