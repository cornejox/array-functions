<template>

    <div class="fixed w-full z-10">
        <nav class="flex justify-between bg-black text-white bg-clip-content bg-top h-full">
            <div class="px-5 xl:px-12 py-6 flex w-full items-center space-x-4">
                <span class=" text-2xl font-bold">
                    {{ header }}
                </span>
            </div>
        </nav>
    </div>

    <div class="p-20 grid grid-cols-2 place-items-center h-screen lim banner">
        <div>
            <div class="p-3 grid place-items-center border-2">
               Arreglo: {{ data_array }}  
            </div>

            <div class="p-3 grid place-items-center border-2">
                Cantidad: {{ array_amount }}
            </div>

            <div class="p-3 grid place-items-center border-2">
                Minimo: {{ array_min }} 
            </div>

            <div class="p-3 grid place-items-center border-2">
                Máximo: {{ array_max }}
            </div>

            <div class="p-3 grid place-items-center border-2">
                Promedio: {{ array_prom }}
            </div>    

            <div class="p-3 grid place-items-center border-2">
                {{ data_array3 }}
            </div>                                            
            <br>
            <input
                v-model="data"
                class="border-2 placeholder:italic placeholder:text-slate-400 block bg-white w-full border border-slate-300 rounded-md py-2 pl-9 pr-3 shadow-sm focus:outline-none focus:border-sky-500 focus:ring-sky-500 focus:ring-1 sm:text-sm" 
                placeholder="Write elements..." 
                type="number"
                onfocus="this.value=''">

            <div class="pt-7 pr-2 pb-7 pl-2">
                <button
                    @click="addStart()"
                    class=" px-7 border border-gray-300 text-gray-700 rounded-md py-2 m-2 transition duration-500 ease select-none hover:bg-gray-300 focus:outline-none focus:shadow-outline">
                        agregar al principio
                </button>
                <button
                    @click="removeStart()"
                    class=" px-7 border border-gray-300 text-gray-700 rounded-md py-2 m-2 transition duration-500 ease select-none hover:bg-gray-300 focus:outline-none focus:shadow-outline">
                        Eliminar del principio
                </button>
            </div>
            <div class="pt-0 pr-2 pb-10 pl-2">
                <button
                    @click="addEnd()"
                    class=" px-11 border border-gray-300 text-gray-700 rounded-md py-2 m-2 transition duration-500 ease select-none hover:bg-gray-300 focus:outline-none focus:shadow-outline">
                        Agregar al final
                </button>
                <button
                    @click="removeEnd()"
                    class=" px-11 border border-gray-300 text-gray-700 rounded-md py-2 m-2 transition duration-500 ease select-none hover:bg-gray-300 focus:outline-none focus:shadow-outline">
                        Eliminar del final
                </button>           
            </div>                              
        </div>

        <div>
            <div class="p-3 grid place-items-center border-2">
               Arreglo: {{ data_array_ }}  
            </div>

            <div class="p-3 grid place-items-center border-2">
                Cantidad: {{ array_amount2 }}
            </div>

            <div class="p-3 grid place-items-center border-2">
                Minimo: {{ array_min2 }} 
            </div>

            <div class="p-3 grid place-items-center border-2">
                Máximo: {{ array_max2 }}
            </div>

            <div class="p-3 grid place-items-center border-2">
                Promedio: {{ array_prom2 }}
            </div>    

            <div class="p-3 grid place-items-center border-2">
                {{ data_array3 }}
            </div>                                            
            <br>
            <input
                v-model="data_"
                class="border-2 placeholder:italic placeholder:text-slate-400 block bg-white w-full border border-slate-300 rounded-md py-2 pl-9 pr-3 shadow-sm focus:outline-none focus:border-sky-500 focus:ring-sky-500 focus:ring-1 sm:text-sm" 
                placeholder="Write elements..." 
                type="number"
                onfocus="this.value=''">

            <div class="pt-7 pr-2 pb-7 pl-2">
                <button
                    @click="addStart2()"
                    class=" px-7 border border-gray-300 text-gray-700 rounded-md py-2 m-2 transition duration-500 ease select-none hover:bg-gray-300 focus:outline-none focus:shadow-outline">
                        agregar al principio
                </button>
                <button
                    @click="removeStart2()"
                    class=" px-7 border border-gray-300 text-gray-700 rounded-md py-2 m-2 transition duration-500 ease select-none hover:bg-gray-300 focus:outline-none focus:shadow-outline">
                        Eliminar del principio
                </button>
            </div>
            <div class="pt-0 pr-2 pb-10 pl-2">
                <button
                    @click="addEnd2()"
                    class=" px-11 border border-gray-300 text-gray-700 rounded-md py-2 m-2 transition duration-500 ease select-none hover:bg-gray-300 focus:outline-none focus:shadow-outline">
                        Agregar al final
                </button>
                <button
                    @click="removeEnd2()"
                    class=" px-11 border border-gray-300 text-gray-700 rounded-md py-2 m-2 transition duration-500 ease select-none hover:bg-gray-300 focus:outline-none focus:shadow-outline">
                        Eliminar del final
                </button>           
            </div>                              
        </div>   

    </div>

</template>

<script>
import { ref, computed } from 'vue'

    export default {

        setup() {

            //// data ////
            let data = ref()
            let data_ = ref()

            //// data feed ////
            let data_array = ref([])
            let data_array_ = ref([])

            //// ARRAY FUNCTION (1) ////

            // unshift - Agrega al inicio //
            const addStart = () => {
                data_array.value.unshift(data.value)
            }

            // pop - Elumina el final //
            const removeEnd = () => {
                data_array.value.pop()
            }

            // push - Agrega al final //
            const addEnd = () => {
                data_array.value.push(data.value)
            }

            // shift - Elimina al inicio //
            const removeStart = () => {
                data_array.value.shift()
            }

            //// COMPUTED ////

            // Encontrar la longitud
            const array_amount = computed(() => {
                return data_array.value.length
            })

            // Máximo del array
            const array_max = computed(() => {
                let max = Math.max(...data_array.value)

                if(max == -Infinity){
                    max = 0
                }

                return max
            })

            // Minimo del array
            const array_min = computed(() => {
                let min = Math.min(...data_array.value)

                if(min == Infinity){
                    min = 0
                }
                
                return min
            })

            // Promedio del array
            /*Aplica una función a un acumulador y a cada valor de una array (de izquierda a derecha) 
            para reducirlo a un único valor */
            const array_prom = computed(() => {

                if(data_array.value.length == 0){
                    return
                }

                let sum = data_array.value.reduce((previous, current) => current += previous)
                let prom = sum / data_array.value.length

                return prom
            })

            //// ARRAY FUNCTION (2) ////

            // unshift - Agrega al inicio //
            const addStart2 = () => {
                data_array_.value.unshift(data_.value)
            }

            // pop  - Elimina al final //
            const removeEnd2 = () => {
                data_array_.value.pop()
            }

            // push - Agrega al final //
            const addEnd2 = () => {
                data_array_.value.push(data_.value)
            }

            // shift - Elimina al inicio //
            const removeStart2 = () => {
                data_array_.value.shift()
            }

            //// COMPUTED ////

            // Encontrar la longitud
            const array_amount2 = computed(() => {
                return data_array_.value.length
            })

            // Máximo del array
            const array_max2 = computed(() => {
                let max = Math.max(...data_array_.value)

                if(max == -Infinity){
                    max = 0
                }

                return max
            })

            // Minimo del array
            /* ... transformamos la variable numeros en una lista de argumentos,
            es como si le quitáramos los corchetes ( “[]” ) al array */
            const array_min2 = computed(() => {
                let min = Math.min(...data_array_.value)

                if(min == Infinity){
                    min = 0
                }
                
                return min
            })

            // Promedio del array
            const array_prom2 = computed(() => {

                if(data_array_.value.length == 0){
                    return
                }

                let sum = data_array_.value.reduce((previous, current) => current += previous)
                let prom = sum / data_array_.value.length

                return prom
            })

            //// ECUACIÓN //// 

            // arr_3 =  arr_1 * 2 + ( arr_2  / 2 )
            const data_array3 = computed (() => {

                let message = "Las matrices contienen diferentes tamaños"

                if(array_amount.value == 0 && array_amount2.value == 0){
                    let message = " Sin datos sobre los arreglos "
                    return message
                }
                else if(array_amount.value == array_amount2.value){

                    let mult_3  = []

                        let mult_1 = data_array.value.map(response => (response * 2) )

                        let mult_2 = data_array_.value.map(response => (response) )

                    for (let index = 0; index < data_array.value.length; index++) {
                        mult_3[index] = mult_1[index] + (mult_2[index] / 2)

                    }
                    return mult_3
                }                

                return message
            })            

            return {
                // array 1
                data,
                data_array,

                // array 2
                data_,
                data_array_,

                // tittle
                header: 'Funciones de arreglos',

                //functions - 1
                addStart,
                removeEnd,
                addEnd,
                removeStart,

                //functions - 2
                addStart2,
                removeEnd2,
                addEnd2,
                removeStart2,                
                
                //computed - 1
                array_amount,
                array_max,
                array_min,
                array_prom,
                data_array3,

                //computed - 2
                array_amount2,
                array_max2,
                array_min2,
                array_prom2                
            }
        }
    }
</script>

<style>
    .lim{
        max-width: 1920px;
        max-height: 1080px;
        min-width: 1000px;
        min-height: 500px;
    }

    .banner{
        background-image: url("https://pixabay.com/get/g0be1b9e7c0d9f14495609aae2e6839589b8551c9d7ec37ea465b5c40378d06617f47d8bb45b6507afbe4cc64e211e9bf.jpg");
        background-position: center center;
        background-repeat: no-repeat;
        background-attachment: fixed;
        background-size: cover;
    }
</style>