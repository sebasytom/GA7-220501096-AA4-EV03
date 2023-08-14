<template>
    <div class="container">
        <h1>Formulario de Cliente</h1>
        <form id="customer-form" @submit.prevent="guardar">

            <div class="form-group">
                <label for="codigo"><b>Código:</b></label>
                <input type="number" id="codigo" name="codigo" required v-model="codigo"/>
            </div>

            <div class="form-group">
                <label for="nombre"><b>Nombre:</b></label>
                <input type="text" id="nombre" name="nombre" required v-model="nombre"/>
            </div>

            <div class="form-group">
                <label for="apellido"><b>Apellido:</b></label>
                <input type="text" id="apellido" name="apellido" required v-model="apellido"/>
            </div>

            <div class="form-group">
                <label for="dirección"><b>Dirección:</b></label>
                <input type="text" id="direccion" name="dirección" required v-model="dirección"/>
            </div>

            <div class="form-group">
                <label for="talla"><b>Talla:</b></label>
                <input type="text" id="talla" name="talla" required v-model="talla"/> 
            </div>

            <div class="form-group">
                <label for="telefono"><b>Telefono:</b></label>
                <input type="text" id="telefono" name="telefono" required v-model="telefono"/>
            </div>
            
            
            <button type="submit" class="button1" name="guardar">Guardar</button><br />
            <button type="button" class="button1" name="eliminar" @click="eliminar">Eliminar</button><br />
            <button type="button" class="button1" name="actualizar" @click="actualizar">Actualizar</button><br />
            <button type="button" class="button1" name="consultar" @click="consultar">Consultar</button><br />
        </form>
    </div>
</template>


<script>
import axios from "axios";

export default{

    data(){

        return{
            codigo: "",
            nombre: "",
            apellido: "",
            dirección:"",
            talla: "",
            telefono:"",
        };
    },

    methods: {

        guardar() {

            axios
                .post("http://localhost:8080/api/clientes", {
                    codigo: this.codigo,
                    nombre: this.nombre,
                    apellido: this.apellido,
                    dirección: this.dirección,
                    talla: this.talla,
                    telefono: this.telefono,
                })
                .then((response) => {
                    console.log("Cliente registrado con exito:", response.data);
                    alert("éxito");
                    this.codigo = '';
                    this.nombre = '';
                    this.apellido = '';
                    this.dirección = '';
                    this.talla = '';
                    this.telefono = '';
                })
                .catch((error) => {
                    console.error("Error al registrar el cliente:", error);
                });
        },

        actualizar() {

            axios
                .put("http://localhost:8080/api/clientes/actualizar/"+this.codigo, {
                    codigo: this.codigo,
                    nombre: this.nombre,
                    apellido: this.apellido,
                    dirección: this.dirección,
                    talla: this.talla,
                    telefono: this.telefono,
                })
                .then((response) => {
                    console.log("Cliente actualizado con éxito:", response.data);
                })
                .catch((error) => {
                    console.error("Error al actualizar cliente:", error);
                });
        },

        consultar() {

            axios
                .get('http://localhost:8080/api/clientes/'+this.codigo)
                .then((response) => {
                    //Actualizar los campos del formulario con los datos del cliente consultado
                    this.nombre = response.data.nombre;
                    this.apellido = response.data.apellido;
                    this.dirección = response.data.dirección;
                    this.talla = response.data.talla;
                    this.telefono = response.data.telefono;
                })
                .catch((error) => {
                    console.error("Error al consultar cliente:", error);
                });
        },

        eliminar() {

            axios
                .delete("http://localhost:8080/api/clientes/"+this.codigo)
                .then(() => {
                    console.log("Cliente eliminado con éxito");
                    //limpiar los campos del formulario después de eliminar
                    this.codigo = "";
                    this.nombre = "";
                    this.apellido = "";
                    this.dirección = "";
                    this.talla = "";
                    this.telefono = "";
                })
                .catch((error) => {
                    console.error("Error al eliminar cliente:",error);
                });
        },          
    },           
};             
</script>
                