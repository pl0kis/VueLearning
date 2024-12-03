<template>
  <div className="user">
    <h3>Имя пользователя - {{ user.name }}</h3>
    <p>Пароль пользователя - {{ user.pass }} && Почта пользователя - <b>{{ user.email }}</b></p>
    <button @click="deleteUser(index)">Удалить</button>
  </div>
</template>

<script>
export default {
    props:{
        user:{
            type: Object,
            required: true,
        },
        index:{
            type:Number,
            required:true,
        },
        deleteUser:{
            type: Function,
            required:true,
        }
    }
}
</script>

<style scoped>
.user{
    background-color: rgb(184, 231, 231);
    border: 1px solid rgb(0, 0, 0);
    padding: 30px;
    margin-top: 10px;
}
.user button{
    background-color: rgb(202, 178, 224);
    width: 200px;
    height: 50px;
    border-radius: 10px;
    cursor: pointer;  
    transition: 0.3s;
    font-size: 20px;
    color: rgb(52, 53, 53);
    border: none;
}
.user button:hover{
    background-color: rgb(152, 141, 163);
    transition: 0.3s;
}
</style>