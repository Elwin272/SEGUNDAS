<template>
    <div class="w-full flex flex-row">

        <div class=" w-1/2 flex flex-col gap-y-5 py-5 px-10 overflow-y-scroll h-[900px]">

            <div v-for="Cli, i in clients" :key="Cli.id"
                class="w-full border-2 rounded border-black p-3 flex flex-col gap-y-3">

                <h2 class="text-3xl font-bold"> Usuario: {{ Cli.username }}</h2>

                <div class=" w-full flex flex-col gap-y-2">
                    <h2 class="text-xl font-semibold"> Informacion personal:</h2>
                    <div class="w-full flex flex-col gap-y-1">

                        <div class="w-full flex flex-row gap-x-6">
                            <h3> Nombre: {{ Cli.name }}</h3>
                            <h3> Correo electronico: {{ Cli.email }}</h3>
                        </div>

                        <div class="w-full flex flex-row gap-x-6">
                            <h3> Numero de telefono: {{ Cli.phone }}</h3>
                            <h3> Pagina web: {{ Cli.website }}</h3>
                        </div>

                        <div>
                            <h2>Direccion: Calle {{ Cli.address.street }} en la habitacion {{ Cli.address.suite }}, {{
                                Cli.address.city }}, {{ Cli.address.zipcode }}</h2>
                        </div>
                    </div>
                </div>

                <div class=" w-full flex flex-col gap-y-2">
                    <h2 class="text-xl font-semibold"> Informacion empresarial:</h2>
                    <div class="w-full flex flex-col gap-y-1">

                        <h3> Nombre de la empresa: {{ Cli.company.name }}</h3>
                        <h3> Aspectos que caracterizan a la compania: {{ Cli.company.catchPhrase }}</h3>
                        <h3> Algunos de sus puntos mas fuertes: {{ Cli.company.bs }}</h3>

                    </div>
                </div>

                <button class="w-full border bg-blue-600 border-blue-800 text-white rounded-full"
                    @click="$router.push('/comentarios/' + Cli.id)"> Ver comentarios </button>

            </div>
        </div>

    </div>
</template>

<script>
import axios from 'axios';


export default {

    data() {
        return {
            coments: null,
            clients: null

        }

    },
    mounted() {
        this.getcoments();
        this.getclients();
    },
    methods: {
        getcoments() {
            axios.get('https://jsonplaceholder.typicode.com/posts').then(
                response => {
                    this.coments = response.data
                }
            );
        },
        getclients() {
            axios.get('https://jsonplaceholder.typicode.com/users').then(
                response => {
                    this.clients = response.data
                }
            );
        }
    }

}
</script>