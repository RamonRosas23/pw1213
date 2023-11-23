<template>
    <div class="MaestrosLista">
        Hola maestros <br>
        <table class="tabla">
            <thead class="body">
                <th>Clave</th>
                <th>Nombre</th>
                <th>Departamento</th>
                <th>Estatus</th>
            </thead>
            <tbody class="body">
                <tr v-for="maestro in maestros" :key="maestro.clave">
                    <td>{{ maestro.clave }}</td>
                    <td>{{ maestro.nombre }}</td>
                    <td>{{ maestro.departamento }}</td>
                    <td>{{ maestro.estatus }}</td>
                </tr>
            </tbody>
        </table>
    </div>
</template>
<script>
import axios from 'axios';
import { URL_DATOS } from '../utils/constantes';
    export default {
        name: "MaestrosLista",
        data(){
            return{
                maestros: []
            }
        },
        created(){
            this.traeMaestros();
        },
        methods:{
            traeMaestros: async function(){
                let m = [];
                await axios.get(URL_DATOS+"/maestros")
                .then(function(response){
                    console.log(response.data);
                    m = response.data;
                });
                this.maestros = m;
            }
        }
    }
</script>