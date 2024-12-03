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
    },
    deleteUser(index){
      this.users.splice(index, 1)
    }
  }
 }
</script>

<template>
  <div className="main">
    <h3>Форма добавления пользователей</h3>
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

  <User v-for="(el,index) in users" :key="index" :user="el" :index="index" :deleteUser="deleteUser"/>
  </div>

</template>

<style scoped> 
.main{
  display: flex;
  flex-direction: column;
  width: 600px;
  margin: 0 auto;
  background-color: beige;
  padding: 10px;
}
.main input{
  padding: 10px;
  margin-top: 10px;
  border-radius: 5px;
  border: 1px solid green;
}
.main button{
  background-color: green;
  width: 200px;
  height: 40px;
  margin: 0 auto;
  color: azure;
  border-radius: 5px;
  border: none;
  cursor: pointer;
  transition: 0.3s;

}
.main button:hover{
  background-color: rgb(5, 92, 5);
  transition: 0.3s;
}
</style>
