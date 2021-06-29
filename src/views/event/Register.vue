<template>
    <p>Registration form here</p>
    <button @click="register">Register Me!</button>
</template>

<script>
export default {
  props: ['event'],
  inject: ['GStore'], // <---- Inject the Global Store
  methods: {
    register() {
      // If registration API call is successful
      this.GStore.flashMessage =
        'You are successfully registered for ' + this.event.title
      setTimeout(() => {  // After 3 seconds remove it
        this.GStore.flashMessage = ''
      }, 3000)


      // Push back to the event details
      this.$router.push({
        name: 'EventDetails',
        params: { id: this.event.id }
      })
    }
  }
}
</script>
