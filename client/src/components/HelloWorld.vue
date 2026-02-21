<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <p>Welcome to the MEVN stack boilerplate.</p>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: {
      type: String,
      required: true
    }
  }
}
</script>
