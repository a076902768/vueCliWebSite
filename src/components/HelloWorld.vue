<template>
  <div class="hello">
    <a href="#" @click.prevent="signout">登出</a>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  },
  methods: {
    signout: function(){
      const api=`${process.env.APIPATH}/logout`;
      const vm=this;

      this.$http.post(api).then((response) => {
        console.log(response.data);
        if(response.data.success == true) {
          vm.$router.push('/login');//if 登出成功 則將vue router的虛擬路徑改回@/login(登入頁面)
        }
      });
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
