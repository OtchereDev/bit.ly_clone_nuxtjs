<template>
    <form @submit.prevent="handleSubmit" class="mb-10 w-full">      
        <input v-model="url" placeholder="Paste Your Long links here" type="text" class="w-full p-2 placeholder-gray-500 block outline-none bg-gray-100 rounded-lg shadow-lg my-4">
        <button class="block py-2 bg-blue-500 w-full focus:outline-none rounded-lg shadow-md text-gray-100 font-semibold">Shorten !</button>
    </form>
</template>

<script>

export default {
    data(){
        return {
            url:'',
        }
    },
    methods:{
        async handleSubmit(){
            try {
                const fd=new FormData()
                fd.append("original_link", this.$data.url)
    
                const res = await fetch("http://localhost:8000/api/create/",{
                    
                    method:'POST',
                    body:fd
                    
                })

                if(!res.ok){
                    throw Error('cant handle request')
                }

               const data=await res.json()

               this.$data.url=''

               this.$emit('ShortenedLink',data['shortened_link'])

                
                
            } catch (err) {
                console.log(err.message)
            }   

        }
    }
}
</script>

<style>

</style>