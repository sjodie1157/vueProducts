<template>
  <div class="wrapper">
    <!-- displaying the array -->

    <div class="row" v-if="products.length">
      <!-- can shorten by only checkoing for ...v-if="products"... -->
      <!-- product can be any keyword & :key is to make it unique by using the id(is using v-for)-->
      <div class="prodCard" v-for="product in products" :key="product.id">
        <!-- products inside the array -->
        <div class="card-header">
          <h3>{{ product.prodName }}</h3>
        </div>
        <div class="card-body">
          <!-- using bind (do not include "{{  }}") -->
          <img @mouseenter="onMouseEnter" @mouseleave="onMouseLeave" :src="product.image" :alt="product.prodName" loading="lazy">
          <!-- if amount is more than R 420.00 apply class cheap and expensive using ternary operators  -->
          <p :class="product.amount > 420 ? 'expensive' : 'cheap'">R {{ product.amount.toFixed(2) }}</p>
          <!-- shortcut ...:class="{expensive : product.amount> 420}"... -->
        </div>
        <div class="card-footer">
          <a href="#" type="button">View Detail</a>
        </div>
      </div>
    </div>

    <!-- add else under if div -->
    <div v-else>
      <h2>No Products</h2>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {

    // data() {} is also refured as a reactive state

    // data is a factory function because it has a return function

    return {

      // creating objects by the use of a colon ":"

      products: 
      [
                    {
                        id: 1,
                        prodName: 'Python Crash Course',
                        category: 'Python',
                        amount: 400.9999,
                        image: 'https://i.postimg.cc/MKDLBPYm/Python-Crash-Course-cover.jpg'
                    },
                    {
                        id: 2,
                        prodName: 'Python Programming',
                        category: 'Python',
                        amount: 900.4586,
                        image: 'https://i.postimg.cc/rFcbKX5p/Python-Programming-for-Beginners-cover.jpg'
                    },
                    {
                        id: 3,
                        prodName: 'Mastering C++',
                        category: 'C++',
                        amount: 1800.896,
                        image: 'https://i.postimg.cc/Ss9zrpfT/Mastering-C-Programming.jpg'
                    }
                ]
          }
        },
  components: {

    //used to adding external components
    
  },
  methods: {
    onMouseEnter() {
      alert('Mouse has entered')
    },
    onMouseLeave() {
      alert('Mouse has left')
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.wrapper :is(.row) {
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
}

.prodCard {
  width: 18rem;
}

.prodCard :is(>*, img){
  width: 100%;
  aspect-ratio: 1/1;
}

.expensive {
  font-weight: bolder;
  color: darkkhaki;
}

.cheap {
  color: black;
}
</style>
