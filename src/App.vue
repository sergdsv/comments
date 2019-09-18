<template>
  <div id="app">

    <button @click="getArray">sfdwe</button>
  </div>
</template>

<script>
import Comment from './components/Comment.vue'

export default {
  name: 'app',
  components: {
    Comment
  },
  data() {
    return {
      comments: [],
      arr: [
            {id: 1, title: 'hello1', parent: 0},
            {id: 2, title: 'hello2', parent: 0},
            {id: 3, title: 'hello3', parent: 1},
            {id: 4, title: 'hello4', parent: 1},
            {id: 5, title: 'hello5', parent: 4},
            {id: 6, title: 'hello6', parent: 4},
            {id: 7, title: 'hello7', parent: 3},
            {id: 8, title: 'hello8', parent: 2}
      ],
      arr_out: [],
      // parrent: ''
    }
  },

  methods: {
            getNested(arr) {
                const output = []
                 arr.forEach(i => {
                   if (i.parent == 0){
                      this.arr_out.push(i)
                      const parent = i.id
                        arr.forEach(i => {
                          if(i.parent == parent){
                            this.arr_out.push(i.children = i)
                          }
                        })
                   }
                   
                 });
            },


            getArray: function() {
                this.getNested(this.arr)
            }
        },


  mounted() {
        
  }

}
</script>

<style>

</style>
