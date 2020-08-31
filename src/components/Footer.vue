<template>
  <v-card height="400px">
    <v-footer fixed padless>
      <v-card flat tile width="100%" class="red lighten-1 text-center">
        <v-card-text class="white--text">
          Icons made by
          <a
            href="https://www.flaticon.com/authors/freepik"
            style="text-decoration: none; color: white;"
            title="Flaticon"
          >Freepik</a>
          from
          <a
            href="https://www.flaticon.com/"
            style="text-decoration: none; color: white;"
            title="Flaticon"
          >www.flaticon.com</a>
          <span class="ma-3">·</span>
          secured by
          <v-btn small class="ml-2" color="indigo" dark href="https://snyk.io">Snyk.io</v-btn>
          <span class="ma-3">·</span>
          deployed on
          <v-btn small class="ml-2" color="info" dark href="https://netlify.com">Netlify</v-btn>

          <div>
            {{ new Date().getFullYear() }}
            <strong>© Liran Tal</strong>

            <span class="ml-1"></span>
            <v-btn v-for="(item, i) in icons" :key="i" :href="item.url" class="mx-auto" icon>
              <v-icon size="24px">{{ item.icon }}</v-icon>
            </v-btn>
          </div>
        </v-card-text>
      </v-card>
    </v-footer>
  </v-card>
</template>

<script>
export default {
  data: () => ({
    icons: [
      { icon: "mdi-twitter", url: "https://twitter.com/liran_tal" },
      { icon: "mdi-github", url: "https://github.com/lirantal" }
    ]
  })
};
</script>