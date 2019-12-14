<template>
   <div>
     <b-nav>
    <b-nav-item active>Fancy Quiz App</b-nav-item>
    <b-nav-item>Questions {{num_correct}}/{{num_total}}</b-nav-item>
  </b-nav>
   </div>
</template>


<script>
 
  export default {
    props: [
      'num_correct',
      'num_total'
    ]
  }

</script>