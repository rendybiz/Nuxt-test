<template>
  <div class="container">
    test {{JSON.stringify(project)}}
    <div>
      <ul>
        <li>
          <nuxt-link to="/">home</nuxt-link>
        </li>
      </ul>
      <!-- <logo /> -->
    </div>

    <div>
      <!-- {{JSON.stringify(anotherData)}} -->
      <h1 class="title">nuxt-test</h1>
      <h2 class="subtitle">first test</h2>
    </div>
  </div>
</template>

<script>
import Logo from "~/components/Logo.vue";
import axios from "axios";

export default {
  data() {
    return {
      project: [],
      anotherData: []
    };
  },
  // asyncData() {
  //   return new Promise(function(resolve, reject) {
  //     //do something
  //     const config = {
  //       headers: {
  //         Accept: "application/json",
  //         Api_key:"41418C656335D6BA2B58C9F5B404CCF0B894070466F0D038D6B991F9F67B70B6"
  //       }
  //     };
  //     const url = "http://api2.dev.locard.co.id/f3/v1/member/guest_login";
  //     try {
  //       let fn = async function (){
  //         const res = await axios.post(url, config);
  //         var tResolve = {};
  //         tResolve.project = res.data;
  //         console.log(" response is here", res.data);
  //         resolve(tResolve)
  //       };
  //       fn();
  //     } catch (e) {
  //       console.log("e");
  //       reject(e)
  //     }
  //   });
  // },
  async created() {
    console.log("Hello");
    const config = {
      headers: {
        "Accept": "application/json",
        "Api_key":
          "41418C656335D6BA2B58C9F5B404CCF0B894070466F0D038D6B991F9F67B70B6"
      }
    };
    const url = "http://api2.dev.locard.co.id/f3/v1/member/guest_login";

    try {
      const res = await axios.post(url,{}, config);
      this.anotherData = res.data;
    } catch (e) {
      console.log("e", e);
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
        }
      ]
    };
  }
};
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

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
