<template>
  <v-app>
    <v-main>
      <Hero />
      <Tips />
      <v-container class="text-center pb-10" fluid="true">
        <span class="mr-2">Not convinced?</span>
        <v-btn
          color="grey"
          href="https://github.com/lirantal/no-secrets-env-vars-website"
          outlined
          large
        >
          <span class="grey--text text--darken-1 font-weight-bold">Discuss on GitHub</span>
        </v-btn>
      </v-container>
    </v-main>
    <Footer />
  </v-app>
</template>

<script>
import Hero from "./components/Hero";
import Tips from "./components/Tips";
import Footer from "./components/Footer";

export default {
  name: "App",
  components: {
    Hero,
    Tips,
    Footer
  }
};
</script>