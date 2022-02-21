<template>
  <v-app>
    <v-layout wrap>
      <v-flex class="header d-flex align-center justify-center"
        ><v-btn icon><v-icon>mdi-music</v-icon></v-btn>
        <h1 class="font-weight-light pa-3 bold">Welcome to Music</h1>
        <v-btn icon><v-icon>mdi-music</v-icon></v-btn>
      </v-flex>
      <v-main>
        <router-view />
      </v-main>
    </v-layout>
  </v-app>
</template>

<script>
export default {
  name: "App",
};
</script>

<style>
#app {
  background: rgb(255, 255, 255);
  background: radial-gradient(
    circle,
    rgba(255, 255, 255, 0) 0%,
    rgba(81, 114, 153, 0.4668461134453782) 100%
  );
  color: rgb(57, 53, 53);
}
a {
  color: rgba(255, 255, 255, 0.714);
  font-family: "Montserrat", sans-serif;
  background: rgb(60, 65, 133);
  background: radial-gradient(
    circle,
    rgba(60, 65, 133, 0.7217480742296919) 0%,
    rgba(27, 200, 202, 0.5228685224089635) 100%
  );
}
.header {
  background: radial-gradient(
    circle,
    rgba(255, 255, 255, 0) 0%,
    rgba(81, 114, 153, 0.4668461134453782) 100%
  );
}
</style>
