<template>
    <div id="Juegos">
        <h1>Componente Juegos</h1>

        <div class="contenedorPadre">
                <div v-for="(juego,index) in juegos" v-bind:key="index" class="card m-2" style="width: 18rem;">
                        <img v-bind:src="juego.background_image" class="card-img-top" alt="logo">
                        <div class="card-body">
                            <h5 class="card-title">{{juego.name}}</h5>
                            <p class="card-text">ESRB Rating: {{  juego.esrb_rating.name }}</p>
                        </div>
                        <ul class="list-group list-group-flush">
                            <li class="list-group-item">Rating: {{ juego.rating }}</li>
                            <li class="list-group-item">Released: {{  juego.released }}</li>
                            <li class="list-group-item">Updated: {{  juego.updated }}</li>
                        </ul>
                        <div class="card-body">
                            <a v-on:click="mostrarOpiniones(juego.name)" class="btn btn-primary">Opinar</a>
                            <a v-on:click="irAdministracion(juego.name)" class="btn btn-danger">Like</a>
                        </div>
                </div>
        </div>

    </div>

    <footer>
            <div class="center">
                <p>
                    &copy; Todos los derechos resservados
                </p>
            </div>
        </footer>
</template>



<script>
import axios from 'axios';
export default{
    name:'Juegos',
    data:function(){
        return{
            cantidadJuegos:0,
            juegos:[],
        }
    },
    methods:{
        consumirApi:function(){

            // let url='https://api.rawg.io/api/games?key=77c79575495e4380b43ff38d0f1cb43f';
            let url='https://api.rawg.io/api/games?key=548ac8fcc5ad4b3780b81ed0b0a992c6';
            axios(url)
            .then(respuesta =>{
                // console.log(respuesta);
                this.cantidadJuegos = respuesta.data.results.length;
                // lógica para acumular en el arreglo juegos cada juego de las distintas paginas
                for(let i=0; i < this.cantidadJuegos; i++){
                    // console.log(respuesta.data.results[i]);
                    this.juegos.push(respuesta.data.results[i]);
                }
            })
            .catch(error=>{
                console.log(error);
            });
        },
        mostrarOpiniones:function(nombreJuego){
            this.$router.push(`/opiniones/${nombreJuego}`);
        },
        irAdministracion:function(nombreJuego){
            this.$router.push(`/administracion/${nombreJuego}`);
        },
    },
    created(){
        this.consumirApi();
    }
}
</script>

<style scoped>
#Juegos{
    background: rgba(94,179,86,1);
    background: -moz-linear-gradient(left, rgba(94,179,86,1) 0%, rgba(22,136,12,1) 100%);
    background: -webkit-gradient(left top, right top, color-stop(0%, rgba(94,179,86,1)), color-stop(100%, rgba(22,136,12,1)));
    background: -webkit-linear-gradient(left, rgba(94,179,86,1) 0%, rgba(22,136,12,1) 100%);
    background: -o-linear-gradient(left, rgba(94,179,86,1) 0%, rgba(22,136,12,1) 100%);
    background: -ms-linear-gradient(left, rgba(94,179,86,1) 0%, rgba(22,136,12,1) 100%);
    background: linear-gradient(to right, rgba(94,179,86,1) 0%, rgba(22,136,12,1) 100%);
    filter: progid:DXImageTransform.Microsoft.gradient( startColorstr='#5eb356', endColorstr='#16880c', GradientType=1 );
}

.contenedorPadre{
    display:flex;
    flex-wrap: wrap;
    justify-content: center;
}

a {
    padding: 16px 32px;
    font-size: 24px;
}

a:hover {
    background: linear-gradient(45deg, red, blue, deeppink, blue, red, blue, deeppink, blue);
    background-size: 800%;
    border-radius: 10px;
    filter: blur(0.5px);
    animation: glowing 20s linear infinite;
}

@keyframes glowing {
    0% {
        background-position: 0 0;
    }
    50% {
        background-position: 400% 0;
    }
    100% {
        background-position: 0 0;
    }
}

footer {
    background: #f7f7f7;
    width: 100%;
    height: 70px;
    line-height: 70px;
    color: #444;
}

</style>