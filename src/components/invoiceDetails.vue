<template>
    <div class="panel panel-default">
        <div class="panel-body">
            <input v-if="editMode" type="text" class="form-control" v-model="invoice.nombre_emisor">
            <p v-else>{{ invoice.nombre_emisor }}</p>
        </div>
        <div class="panel-footer">
            <button v-if="editMode" class="btn btn-success" v-on:click="onClickUpdate()">
                Guardar cambios
            </button>
            <button v-else class="btn btn-secondary" v-on:click="onClickEdit()">
                Editar
            </button>
        </div>
    </div>
</template>
<script>
    export default {
        props: ['invoice'],
        data() {
            return {
                editMode: false
            };
        },
        mounted() {
            var ide = this.$route.params.id;
            console.log(ide);
            axios.get(`http://127.0.0.1:8000/api/invoices/${ide}`).then((response) => { // obtener datos de la factura desde la api de laravel
                this.invoice = response.data; // cargar datos de la factura
            });
            console.log(response.data);
        },
        methods: {
            onClickEdit() {
                this.editMode = true;
            },
        }
    }
</script>
