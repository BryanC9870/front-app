<template>
    <div class="container">
        <h3>FACTURAS:</h3>
        <table class="table">
            <thead>
                <tr>
                <th scope="col">ID</th>
                <th scope="col">FECHA</th>
                <th scope="col">EMISOR</th>
                <th scope="col">NIT EMISOR</th>
                <th scope="col">NOMBRE RECEPTOR</th>
                <th scope="col">NIT RECEPTOR</th>
                <th scope="col">VALOR ANTES IVA</th>
                <th scope="col">VALOR IVA</th>
                <th scope="col">VALOR TOTAL</th>
                <th scope="col">DETALLES</th>
                </tr>
            </thead>
            <tbody> 
                <tr v-for="invoice in invoices" v-bind:key="invoice.id"> <!--iteración de array de facturas-->
                    <th scope="row">{{invoice.id}}</th> 
                    <td>{{invoice.fecha_hora}}</td>
                    <td>{{invoice.nombre_emisor}}</td>
                    <td>{{invoice.nit_emisor}}</td>
                    <td>{{invoice.nombre_receptor}}</td>
                    <td>{{invoice.nit_receptor}}</td>
                    <td>{{invoice.valor_antes_iva}}</td>
                    <td>{{invoice.valor_iva}}</td>
                    <td>{{invoice.valor_total}}</td>
                    <td><router-link :to="'/details/' + invoice.id" > Ver datos</router-link></td> <!--redirección a vista de detalles-->
                </tr>
            </tbody>
        </table> 
    </div> 
</template>
<script>
    import axios from 'axios';  // importación de libreria para solitudes http desde el frontend
    export default {
        data() {
            return {
                invoices: [] // declaración de array de facturas
            }
        },
        mounted() {
            axios.get('http://127.0.0.1:8000/api/invoices/index').then((response) => { // petición de los datos a la API de laravel
                console.log(response.data);
                this.invoices = response.data; // cargar las facturas con los datos de la respuesta
            });
        },
        methods: { // declaración de metodos para la manipulación de lo datos
            addInvoice(invoice) {
                this.invoices.push(invoice);
            },
            updateInvoice(index, invoice) {
                this.invoices[index] = invoice;
            },
            deleteInvoice(index) {
                this.invoices.splice(index, 1);
            }
        }
    }
</script>