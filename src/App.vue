<template>
  <v-app>
      <Hero />
      <Tips />
      <v-container class="text-center pb-10" :fluid="true">
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

      <hr/>
      
      <v-container class="text-center pt-10 pb-10" :fluid="true">
        <v-row
          align="center"
          justify="center"
          class="grey lighten-5"
          style="height: 300px;">
          <v-col cols="6">
            <v-sheet
              elevation="12"
              class="pa-12"
            >
              <span class="mr-2">
                <v-text-field 
                  :counter="true"
                  v-model="shareTwitterText"
                  label="tweet"
                  required
                  :error-messages="tweetErrors">
                  </v-text-field>
              </span>
              <br/><br/>
              <v-btn
                color="blue"
                outlined
                large
                @click="shareTwitter"
                class="blue--text text--darken-1 font-weight-bold"
                full-width
              >Share on Twitter
              </v-btn>
            </v-sheet>        
          </v-col>
        </v-row>

      </v-container>

    <Footer />
  </v-app>
</template>

<script>
import Hero from "./components/Hero";
import Tips from "./components/Tips";
import Footer from "./components/Footer";

export default {
  name: "App",
  data: () => {
    return {
      shareTwitterText: "Learn why you should say no to secrets in environment variables: https://goo.gl #NoSecretsEnvVars",
      tweetErrors: []
    }
  },
  components: {
    Hero,
    Tips,
    Footer
  },
  methods: {
    shareTwitter() {
      if (this.shareTwitterText.length > 280) {
        this.tweetErrors.push(`Your text is longer than 280 characters: ${this.shareTwitterText}`)
        return true;
      } else {
        this.tweetErrors = []
        const tweetMsg = encodeURIComponent(this.shareTwitterText)
        const tweetUrl = `https://twitter.com/intent/tweet?text=${tweetMsg}&via=liran_tal`
        window.open(tweetUrl,'_blank');
      }
    }
  }
};
</script>