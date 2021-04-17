<template>
  <div class='text-center text-gray-800'>
      <p>
          redirecting you to <span class="text-blue-400">{{link}}</span>
      </p>
      <p>
          Thank you for using VueDjango URL Shortener
      </p>
  </div>
</template>

<script>
import axios from 'axios'
export default {
    async asyncData ({ params, error }) {
        try {
            const res= await fetch(`http://localhost:8000/api/get_link/`,
            {
                method:'POST',
                headers:{
                    'content-type':'application/json'
                },
                body:JSON.stringify({link:params.link})
            })
            if(!res.ok){
                throw Error('error')
            }
            const data = await res.json()
            // console.log(data.link)
            // location.href=data.link
            return { link: data.link }
        } catch (erro) {
            error({ statusCode: 404, message: 'Post not found' })
        }
  },
  methods:{
      
  },

  data(){
      return{
          name:'oliver'
      }
  },
  beforeMount(){
      
    if(this.$data.link.startsWith('https://')||
       this.$data.link.startsWith('http://')){
          
          console.log(this.$data.link,this.$data.name)
          window.location=this.$data.link

      }else{

          console.log(`http://${this.$data.link}`,this.$data.name)
          window.location=`http://${this.$data.link}`

      }
  }

  
}
</script>

<style>

</style>