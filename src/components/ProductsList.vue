<template>
<div class="container">
    
    <div class="row">
        <h3>MegaDron</h3>
    </div>
    <div class="row">
        <div class="col-12 col-sm-6 col-md-4 ">
            imagen
            <!-- <img :src="producto.imagen"
                :alt="producto.nombre" width="100%"> -->
        </div>
        <div class="col-12 col-sm-6  col-md-8">
            <h6>descripcion Producto</h6>
            <div class="p-3 mb-2 text-white">
                0.00 Bs.
            </div>
            <h5>Color</h5>
            <div>
                <!-- <div v-for="color in producto.colores" :key="color" class="color-box clic" :style="{background: color}" @click="obtenerColor"></div> -->
                <div class="color-box clic" style="background: blue"></div>
                <div class="color-box clic" style="background: black"></div>
            </div>
            <h5>Cantidad</h5>
            <div class="quantity">
                <button @click="disminuir">-</button> <div>{{contador}}</div> <button @click="aumentar">+</button>
            </div>
            <div class="buy-box">
                <button type="button" class="btn btn-primary" :disabled="changeStyle" @click="pedir">Comprar</button>
            </div> 
            
        </div>
    </div>
</div>



<div class="container ">

    <div class="row">
        <h4>Productos relacionados</h4>
    </div>
    <div class="row">
        <div class="col" v-for="producto in products" :key="producto">
            <div class="card" style="width: 18rem;">
                <div class="card-body">
                    <h5 class="card-title">{{producto.nombre}}</h5>
                    <img :src="producto.imagen"
                :alt="producto.nombre" width="200">
                    <p class="card-text">{{producto.descripcion}}</p>
                        <div class="producto-relacionado-precio">Precio:{{producto.precio}} BOB</div>
                    <div>
            <div>
                <div v-for="color in producto.colores" :key="color" class="color-box" :style="{background: color}"></div>
                <!-- <div class="color-box" style="background: blue"></div>
                <div class="color-box" style="background: black"></div> -->
            </div>
                    </div>
                </div>
            </div>
        </div>
        <!-- <div class="col">
            <div class="card" style="width: 18rem;">
                <div class="card-body">
                    <h5 class="card-title"></h5>
                    <img :src="producto.imagen"
                :alt="producto.nombre" width="100%">
                    <p class="card-text">{{producto.nombre}}</p>
                        <div class="producto-relacionado-precio">Precio:{{producto.precio}} BOB</div>
                    <div>
            <div>
                <div class="color-box" style="background: red"></div>
                <div class="color-box" style="background: blue"></div>
                <div class="color-box" style="background: black"></div>
            </div>
                    </div>
                </div>
            </div>
        </div> -->
        <!-- <div class="col">
            <div class="card" style="width: 18rem;">
                <div class="card-body">
                    <h5 class="card-title">Card title</h5>
                    <img src="https://ae01.alicdn.com/kf/S00eb0e55c14f47e2bbf828a92ecd5515U/S6S-Mini-GPS-Drones-150g-Drone-4K-Profesional-HD-Dual-Camera-5G-WIFI-FPV-Brushless-Folding.jpg_Q90.jpg_.webp"
                alt="" width="100%">
                    <p class="card-text">Some quick example text to build on the card title and make up the bulk of
                        the card's content.</p>
                        <div class="producto-relacionado-precio">Precio:1000 BOB</div>
                    <div>
            <div>
                <div class="color-box" style="background: red"></div>
                <div class="color-box" style="background: blue"></div>
                <div class="color-box" style="background: black"></div>
            </div>
                    </div>
                </div>
            </div>
        </div> -->
    </div>
</div>
</template>
<script>
import axios from 'axios'
export default{
    name:'ProductsList',
    data(){
        return{
            products:[],
            contador:1,
            deshabilitado: false
        }
    },
    mounted(){
        axios.get('http://localhost:3000/Productos')
        .then(response => this.products = response.data)
        .catch(error => console.log(error))
    },
    methods:{
        aumentar(){
            this.contador++
        },
        disminuir(){
            if(this.contador > 0){
                this.contador--
            }
        },
    },
    computed:{
        changeStyle(){
            return this.deshabilitado < 1 
        }
    }
}
</script>