<template>
    <div class="Cliente">
        <div class="components">
             <FormularioClientes/>
            <TablaClientes/>
        </div>
    </div>
</template>

<script>
import FormularioClientes from "@/components/FormularioClientes.vue";
import TablaClientes from "@/components/TablaClientes.vue";


export default {
  name: 'ClientesView',

  components: {
    FormularioClientes,
    TablaClientes
  }
}
</script>

<style>
body{
    font-family: Arial, sans-serif;
    background-color: #f0f0f0;
    margin: 0;
    padding: 0;
}

.components{
    display: grid;
    grid-template-columns: 1fr 2fr;
    grid-auto-rows: 1fr;
}

.container{
    /*max-width: 400px;*/
    margin: 1rem;
    padding: 1rem;
    background-color: #fff;
    box-shadow: 0 0 10px  rgba(0, 0, 0, 0.2);
    border-radius: 5px;
}


h1{
    text-align: center;
    margin-bottom: 20px;
}

.form-group label{
    margin-top: 15px;
    text-align: center;
    position: relative;
    font-size: 20px;
    flex-direction: column;
    font-weight: 300;
    display: flex;
    width: 100%;
    justify-content: center; 
    left: 0%;
    margin-bottom: 5px;
}

.form-group input{
    width: 80%;
}



form{
    padding: 2%;
}

label{
    display: block;
    margin-bottom: 5px;
    font-weight: bold;
}

input{
    width: 100%;
    padding: 8px;
    border: 1px solid #ccc;
    border-radius: 3px;
}


.button1{
    border: none;
    width: 85%;
    color: #000000;
    font-size: 15px;
    background: rgb(226, 189, 8);
    padding: 10px;
    border-radius: 5px;
    cursor: pointer;
    position: relative;
    left: 8%;
    text-decoration: none;
    margin-bottom: -7px;
    display: flex;
    align-items: center;
    justify-content: center;
    top: 25px;
}

.button1:hover{
    background: rgb(251, 0, 0);
    color:aliceblue;
}

.table{
    width: 100%;
    border-collapse: collapse;
    margin-bottom: 20px;
}

th, td{
    padding: 10px 40px;
    text-align: center;
    /* border-bottom: 1px solid #ddd;*/
    border-style: solid;
}

tr{
    border-style: solid;
}

th{
    background-color: rgb(226, 189, 8);
    color: #000000;
}

tr:hover{
    background-color: #f5f5f5;
}
</style>