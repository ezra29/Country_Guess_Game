<template>
  <head> 

  </head>

  <body>
    <p v-if="test"> {{ test }}</p>
  </body>
 
</template>

<script>
export default {
  data() {
    return {
      test: "Hallo World",
    }
  },
}
</script>

