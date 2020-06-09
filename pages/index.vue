<template>
  <div class="outer-container">
    <HomeHeader />
    <div class="container">
      <Sidebar/>
      <div>
        <Logo />
        Product Name {{productDetail[0].product_name}}<br/>
        <!-- Product Detail {{JSON.stringify(productDetail)}} -->
        <h1 class="title">nuxt-test</h1>
        <h2 class="subtitle">My fine Nuxt.js project</h2>
        <div class="links">
          <a href="https://nuxtjs.org/" target="_blank" class="button--green">Documentation</a>
          <a href="https://github.com/nuxt/nuxt.js" target="_blank" class="button--grey">GitHub</a>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Logo from "~/components/Logo.vue";
import HomeHeader from "~/components/HomeHeader.vue";
import Sidebar from "~/components/Sidebar.vue";
import axios from "axios";

export default {
  data(){
    return {
      auth:{},
      // productDetail:[]
    }
  },
  // ONLY RENDERED in SERVER SIDE
  async asyncData(context){
    // console.log(" get from env configuration", context.env)
    const auth = process.env.Authorization;

    const config = {
      headers: {
        "Accept": "application/json",
        "Authorization":
          auth
      }
    };

    const productId = '5ebcf0f60ba35271a7636ea0';
    
    const url = "http://api2.dev.locard.co.id/f3/v1/products/" + productId;

    try {
      const res = await axios.get(url, config);
      var productDetail = res.data.result;
      // console.log(" productDetail ", res.data.result)
    } catch (e) {
      console.log("e", e);
    }

    return {
      productDetail: productDetail
    }
  },
  head() {
    return {
      title: "title place",
      meta: [
        {
          hid: "description",
          name: "name of description",
          content: "Best place for content description"
        },
        {
          hid: "product_name",
          name: "Product detail",
          content: this.productDetail[0].product_name
        }
      ]
    };
  },
  async created() {
    // this.auth = process.env.Authorization;
    // console.log("Server Environtment Authentication", process.env.Authorization);

    // const config = {
    //   headers: {
    //     "Accept": "application/json",
    //     "Authorization":
    //       this.auth
    //   }
    // };

    // const productId = '5ebcf0f60ba35271a7636ea0';
    
    // const url = "http://api2.dev.locard.co.id/f3/v1/products/" + productId;

    // try {
    //   const res = await axios.get(url, config);
    //   this.productDetail = res.data;
    //   console.log(" productDetail ", res)
    // } catch (e) {
    //   console.log("e", e);
    // }p
  }, 
  components: {
    Logo,
    Sidebar,
    HomeHeader
  }
};
</script>

<style>
.title {
  font-family: "Quicksand", "Source Sans Pro", -apple-system, BlinkMacSystemFont,
    "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
