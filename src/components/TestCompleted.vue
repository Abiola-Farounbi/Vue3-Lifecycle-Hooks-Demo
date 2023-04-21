
<template>
  <div class="greetings">
    <h1 class="green">{{output}}</h1>
    <p> {{ hello }}</p>
    <button @click="changeMessage">Change </button>

  </div>
</template>

<script>
import { ref,onBeforeMount, onMounted,onBeforeUpdate, onUpdated, onBeforeUnmount, onUnmounted} from 'vue';
export default{
  props:{
  msg: {
    type: String,
    required: true
  }
},
setup(props){
  alert("The creation hook has been initialized");
  
  const output = `${props.msg} - Creation hook`

  onBeforeMount(() => {
    alert('onBeforeMount has been called')
  })

const hello = ref("")

 onMounted ( () =>{
    hello.value = 'welcome to Vue JS';
  })

  const changeMessage = () => {
      hello.value = 'About Vue JS';
  }

  onBeforeUpdate(() => {
  alert('onBeforeUpdate has been called');
  })

  onUpdated(() => {
    alert('onUpdated has been called')
  })

  onBeforeUnmount(() => {
      console.log('OnBeforeUnmount has been called')  
    })

  onUnmounted(() => {
      console.log('OnUnmounted has been called');
  });



  return{output, hello,changeMessage};
}


}

</script>

<style scoped>
h1 {
  font-weight: 500;
  font-size: 2.6rem;
  top: -10px;
}

h3 {
  font-size: 1.2rem;
}

.greetings h1,
.greetings h3 {
  text-align: center;
}

@media (min-width: 1024px) {
  .greetings h1,
  .greetings h3 {
    text-align: left;
  }
}
</style>
