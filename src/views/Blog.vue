<template lang="">
    <div>   
        <Titulo texto="Titulo de mi Blog" />
        <!-- <button @click="consumirApi">Consumir Api</button> -->

        <div v-for="item in arrayBlog" :key="item.id">
            <router-link :to="`/blog/${item.id}`" >
                <ul>
                    <li>{{item.id}} | {{item.title}}</li>
                </ul>
            </router-link>
        </div>
    </div>
</template>
<script>
import Titulo from '../components/Titulo.vue'

export default {
    components: {
        Titulo,
    },
    data () {
        return {
            arrayBlog: []
        }
    },

    methods: {
        async consumirApi() {
            try {
                const data = await fetch("https://jsonplaceholder.typicode.com/posts")
                const array = await data.json()
                console.log(array)
                this.arrayBlog = array
            } catch (error) {
                console.log(error)
            }
        }
    },

    created() {
        this.consumirApi()
    }
}

</script>
<style lang="">
    
</style>