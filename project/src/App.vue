<template>
  <div id="app">
     <div class="khung">
      <img src="./assets/background-01.png" alt="">
      <img src="./assets/text chính-01.png" alt="">
      <img src="./assets/minh hoạ-01.png" alt="">
      <div class="noidung" @submit="onSubmit"  @reset="onReset" >
        <input class="inp" v-model="form.name" type="" placeholder="Tên của bạn" required>
        <input class="inp" v-model="form.email" type="email" placeholder="Email của bạn" required>
        <input class="inp" v-model="form.phone" type="" placeholder="Số điện thoại" required>
        <button class="xn" type="submit" @click="onSubmit">Xác nhận</button>
      </div>
     </div>
    <router-view/>
  </div>
</template>
<script>
export default {
  name: 'App',
  data(){
    return{
      form:{
         name: '',
         email: '',
         phone: ''
      },
       show: true
    }
  },
  methods:{
     onSubmit(event) {
        event.preventDefault()
        alert("Cảm ơn bạn đã để lại thông tin \n"+JSON.stringify(this.form))
         this.form.email = ''
        this.form.name = ''
        this.form.phone = ''
      },
       onReset(event) {
        event.preventDefault()
        // Reset our form values
        this.form.email = ''
        this.form.name = ''
        this.form.phone = ''
        this.show = false
        this.$nextTick(() => {
          this.show = true
        })
      }
  }
}
</script>

<style>
#app {
  width: 100%;
  height: 100%;
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;

}
html, body{
  width: 100%;
  height: 100%;
  padding:0;
  margin: 0;
}
::placeholder{
  color: whitesmoke;
}
.khung{

  margin:auto;
  width: 90%;
  height: 100%;
  position: relative;
}
.noidung{
  position: absolute;
  top: 40%;
  left: 6%;
  width: 48%;
  height: 40%;
}
.inp{
  border-radius: 20px;
  width: 90%;
  height: 16%;
  margin: 2% 1%;
  padding-left: 3%;
  background-color: #62DEC6;
  color: whitesmoke;
  font-size:20px;
  border: none;
}

.xn{
  width: 32%;
  height: 16%;
  color:#62DEC6;
  transform: translateY(10px);
  background-color: whitesmoke;
  border-radius: 20px;
  font-size: 20px;
  padding:2px;
  border:none;
  cursor: pointer;
 
}
img{
  background-size: cover;
  width: 100%;
  height: 100%;
  position: absolute;
  transform: translateX(-50%)
}
</style>
