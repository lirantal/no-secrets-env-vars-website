<template>
  <section id="hero">
    <v-row no-gutters>
      <v-img
        :min-height="'calc(100vh - ' + $vuetify.application.top + 'px)'"
        src="https://images.unsplash.com/photo-1556865897-3e02fedb1774?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=933&q=80"
      >
        <!-- <v-theme-provider dark> -->
          <v-container class="pt-10">
            <v-row align="center" class="white--text mx-auto" justify="center">
              <v-col class="white--text text-center" cols="12" tag="h1">
                <v-sheet color="black" class="pt-12 pb-12" elevation="24">
                  <span
                    :class="[$vuetify.breakpoint.smAndDown ? 'display-1' : 'display-2']"
                    class="white--text font-weight-black"
                  >SAY NO</span>

                  <br />

                  <span
                    :class="[$vuetify.breakpoint.smAndDown ? 'display-3': 'display-2']"
                    class="white--text font-weight-light"
                  >TO SECRETS IN ENVIRONMENT VARIABLES</span>
                </v-sheet>
                <br />
                <v-btn
                  elevation="24"
                  class="align-self black white--text"
                  outlined
                  @click="$vuetify.goTo('#about-me', {duration: 1300, easing: 'easeInQuad'})"
                >
                  <div>Learn why</div>
                  <v-icon>mdi-chevron-double-down</v-icon>
                </v-btn>
              </v-col>
            </v-row>

            <v-row align="center" class="white--text mx-auto">
              <v-col class="white--text">
                <AuthorCard />
              </v-col>
            </v-row>
          </v-container>
        <!-- </v-theme-provider> -->
      </v-img>
    </v-row>
  </section>
</template>

<script>
import AuthorCard from "./AuthorCard";

export default {
  name: "Hero",
  components: { AuthorCard }
};
</script>