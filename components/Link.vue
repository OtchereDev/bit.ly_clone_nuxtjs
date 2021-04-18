<template>
  <div class="w-10/12 mx-auto flex justify-between items-center my-5 bg-gray-500 px-5 py-3 rounded-xl">
      <div>
          <p class="text-gray-50" id='link' >
              {{shortened_link}}
          </p>
      </div>
      <div>
          <button @click="copyDivToClipboard" class="py-1 px-3 bg-blue-500 rounded-lg text-gray-100 focus:outline-none focus:bg-blue-700">
              Copy
          </button>
      </div>
  </div>
</template>

<script>
export default {
    props:['shortened_link'],
    methods:{
         copyDivToClipboard() {
                    // //copy to clipboard type 1
                    // let range = document.createRange();
                    // range.selectNode(document.getElementById("link"));
                    // window.getSelection().removeAllRanges(); // clear current selection
                    // window.getSelection().addRange(range); // to select text
                    // document.execCommand("copy");
                    // window.getSelection().removeAllRanges();// to deselect

                    // //copy to clipboard type2
                    navigator.clipboard.writeText(this.$props.shortened_link)

                    alert('Link copied')

                    this.$emit('copied')
                }
    }
}
</script>

<style>

</style>