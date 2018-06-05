<template>
    <h1>
        <a :href="linkTo" :class="logoClass">
        </a>
    </h1>
</template>

<script>
    export default {
      name: 'logo',
      props: {
        className: {
          type: String
        },
        linkTo: {
          type: String,
          default: '/'
        }
      },
      computed: {
        logoClass() {
          if (this.className) {
            return this.className
          } else {
            return 'logo'
          }
        }
  }
    }
</script>

<style scoped>
  .logo{
    background: url(../../assets/control_panel_logo.png) 0 0 no-repeat;
    display: block;
    width: 256px;
    height: 58px;
    overflow: hidden;
    text-indent: -9999px;
  }
</style>