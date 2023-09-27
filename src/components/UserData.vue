<template>
  <h2>{{ userName }}</h2>
  <h3>{{ age }}</h3>
</template>

<script>
import {
  computed,
  inject,
  onBeforeMount,
  onMounted,
  onBeforeUpdate,
  onUpdated,
  onBeforeUnmount,
  onUnmounted
} from 'vue';
export default {
  props:{
    firstName:{
      type: String,
      default: ''
    },
    lastName:{
      type: String,
      default: ''
    },
    // age:{
    //   type: Number,
    //   default: 0
    // }
  },
    // ['firstName', 'lastName', 'age'],
  setup(props){
    const uName = computed (function(){
      return props.firstName + ' ' + props.lastName
    });

    const age = inject('userAge')

    onBeforeMount(() => {
      console.log('onbeforeMount')
    })
    onMounted( () => {
      console.log('onMount')
    })
    onBeforeUpdate( () => {
      console.log('onBeforeUpdated')
    })
    onUpdated( () => {
      console.log('onUpdated')
    })
    onBeforeUnmount( () => {
      console.log('onBeforeUnmount')
    })
    onUnmounted( () => {
      console.log('onUnmounted')
    })

    return {userName: uName, age}
  }

  // computed: {
  //   userName (){
  //     return this.firstName + ' ' + this.lastName
  //   }
  // }
}
</script>