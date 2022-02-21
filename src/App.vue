<template>
  <v-app>
    <v-main>
      <router-view />
    </v-main>
  </v-app>
</template>

<script>
export default {
  name: "App",
};
</script>

<style>
#app {
  background: rgb(90, 118, 118);
  color: rgb(201, 183, 183);
}
a {
  color: rgb(252, 252, 252);
}
</style>
