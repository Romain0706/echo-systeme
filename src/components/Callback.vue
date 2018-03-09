<template>
  <div class="spinner">
    <p>SPINNING</p>
  </div>
</template>

<script>
export default {
  name: 'callback',
  props: ['auth'],
  data () {
    this.auth.handleAuthentication()
    return {}
  }
}
</script>
