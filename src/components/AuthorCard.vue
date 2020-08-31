<template>
  <div>
    <v-card class="mx-auto mt-10" max-width="404" outlined>
      <v-list-item three-line>
        <v-list-item-content>
          <v-card-text>Let me help you realize why you shouldn't put secrets in environment variables.</v-card-text>
        </v-list-item-content>
      </v-list-item>

      <v-card-actions>
        <v-list-item class="grow">
          <a href="https://twitter.com/liran_tal">
            <v-list-item-avatar color="black darken-3">
              <v-img
                class="elevation-6"
                src="https://github.com/lirantal/Manager-README/blob/master/other/profile-yoda-thumbnail.png?raw=true"
              ></v-img>
            </v-list-item-avatar>
          </a>

          <v-list-item-content>
            <v-list-item-title>Liran Tal</v-list-item-title>
          </v-list-item-content>

          <v-row align="center" justify="end">
            <v-icon class="mr-1">mdi-heart</v-icon>
            <span class="subheading mr-2">256</span>

            <v-icon class="mr-1">mdi-share-variant</v-icon>
            <span class="subheading">45</span>
          </v-row>
        </v-list-item>
      </v-card-actions>
    </v-card>
  </div>
</template>