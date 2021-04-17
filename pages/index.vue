<template>
  <div class="w-full pt-20 bg-gray-200 min-h-screen" >
    <h2 class="text-center text-4xl font-semibold text-green-500 mb-10">
      Nuxt<span class="text-blue-700">Django Url Shortener</span>
    </h2>
    <div class="flex items-center justify-center">
      <div class="w-8/12 flex flex-col justify-center items-center px-10">
        <Form @ShortenedLink='handleShortened' />
        <Link v-if="shortened_link" :shortened_link='shortened_link' @copied='handleCopied' />
      </div>
      <div class="w-2/12 flex justify-center items-center">
        <img :src="require('assets/undraw_link_shortener_mvf6.svg')" alt="link shortener" class="w-full">
      </div>
    </div>
  </div>
</template>

<script>
import Link from '../components/Link'
import Form from '../components/Form'
export default {
  components:{Link,Form},

  data(){
    const shortened_link=null

    return{
      shortened_link
    }
  },

  methods:{
    handleShortened(link){

      let code=link.split('/').slice(-1)
      
      this.$data.shortened_link=`localhost:3000/${code}`
    },
    handleCopied(){
      this.$data.shortened_link=null
    }
  }
}
</script>

<style>
/* Sample `apply` at-rules with Tailwind CSS
.container {
@apply min-h-screen flex justify-center items-center text-center mx-auto;
}
*/
</style>
