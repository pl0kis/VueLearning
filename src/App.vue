<script>
import User from './components/User.vue'

 export default {
  components: { User },
  data(){
    return {
      users:[],
      error:'',
      userName: '',
      userPass: '',
      userEmail: ''
    }
  },
  methods:{
    sendData(){
      if(this.userName == ''){
        this.error = 'Имя не введено'
        return;
      }else if(this.userPass == ''){
        this.error = 'Пароль не введен'
        return;
      }else if(this.userEmail == ''){
        this.error = 'Почта не введена'
        return;
      }

      this.error = ''

      this.users.push({
        name:this.userName,
        pass:this.userPass,
        email:this.userEmail
      })
    }
  }
 }
</script>

<template>
 <input type="text" v-model="userName" placeholder="Имя">
 <input type="password" v-model="userPass" placeholder="Пароль">
 <input type="email" v-model="userEmail" placeholder="Email">
 <p className="error">{{ error }}</p>
  <button @click="sendData()">Отправить</button>
  
  <div v-if="users.length == 0" className="user"> 
    <p>У нас нет пользователей</p>
  </div>
  <div v-else-if="users.length == 1">
    У вас 1 пользователь
  </div>
  <div v-else class="user">
    Массив пользователей имеет больше чем 1 элемент
  </div>


  <div v-for="(el, index) in users" :key="index" className="user">
    <h3>{{ el.name }}</h3>
    <p>{{ el.email }} - <b>{{ el.pass }}</b></p>
  </div>
</template>

<style scoped>

</style>
