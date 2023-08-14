<template>
    <div class="container">
        <h1>Tabla de Clientes</h1>

        <table>
            <thead>
                <tr>
                    <th>Código</th>
                    <th>Nombre</th>
                    <th>Apellido</th>
                    <th>Dirección</th>
                    <th>Talla</th>
                    <th>Telefono</th>               
                </tr>
            </thead>
            <tbody>
                
                <tr v-for="cliente in clientes" :key="cliente.codigo">
                    <td>{{ cliente.codigo }}</td>
                    <td>{{ cliente.nombre }}</td>
                    <td>{{ cliente.apellido }}</td>
                    <td>{{ cliente.dirección }}</td>
                    <td>{{ cliente.talla }}</td>
                    <td>{{ cliente.telefono }}</td>
                </tr>

                <Router-view/>

            </tbody>
        </table>
    </div>
</template>

<script>
import axios from "axios";

export default{
    data(){
        return{
            clientes: [],
        };
    },
    methods: {
        obtenerClientes() {
            //Método para obtener la lista de todos los clientes
            axios.get("http://localhost:8080/api/clientes/listar")
            .then((response) => {
                this.clientes = response.data;
            })
            .catch((error) => {
                console.error("error al obtener clientes:", error);
            });  
        },
    },
    mounted(){
        //llamar al metodo para obtener la lista de clientes al cargar el componente
        this.obtenerClientes();
    },
};

</script>

            



