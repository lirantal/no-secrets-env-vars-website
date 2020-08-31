<template>
  <div>
    <section v-for="(item, i) in tips" :key="i" id="about-me">
      <div class="py-12"></div>

      <v-container class="text-center grey lighten-5 pb-10" fluid="true">
        <h2 class="display-5 font-weight-bold mb-8 mt-8">{{item.title}}</h2>

        <v-responsive class="mx-auto mb-8" width="56">
          <v-divider class="mb-1"></v-divider>

          <v-divider></v-divider>
        </v-responsive>

        <v-responsive
          v-for="(text, y) in item.description"
          :key="y"
          class="mx-auto title font-weight-light mb-8"
          max-width="720"
        >
          <div v-html="text"></div>
        </v-responsive>

        <v-avatar class="elevation-12 mb-12" size="128">
          <v-img v-bind:src="item.image"></v-img>
        </v-avatar>

        <div></div>
      </v-container>

      <div class="py-12"></div>
    </section>
  </div>
</template>

<script>
export default {
  data: () => {
    return {
      tips: [
        {
          title:
            "⚠️ (1) spawned processes share the same environment by default",
          description: [
            "In most languages APIs, the default behavior for spawned child processes is to inhreit the environment variables data from the parent.",
            "Consider the following example:",
            `<code>
 const { spawn } = require('child_process');  
  const ls = spawn('my-program.js', ['/usr']);  
              </code>
            `,
            "The process spawned <code>my-program.js</code> will inherit all the environment variables from <code>process.env</code> of the parent process.` This violates the least privilege principle, where-as different components should only have access to what is explicitly required from them.",
            "What happens if the child process leaks the environment variable data?",
            "As far as audit trail goes - if a leaked happend for environment variables data, how would you track which process is responsible and how did it happen?"
          ],
          image:
            "https://images.unsplash.com/photo-1494368308039-ed3393a402a4?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=2013&q=80"
        },
        {
          title: "⚠️ (2) environment variables are visible in a process list",
          description: [
            "Any user on the system can run a command such as <code>ps -wwwE</code> (for OSX) to list all the system processes and their environment variables.",
            "If the application is compromised in any way that allows the simplest of access to the process list, this data can be easily obtained",
            "Go ahead and try it yourself! In one shell run <code>SECRET_IN_ENV=admin sleep 256</code> and in another shell run <code>ps -wwwE</code> and search for that secret admin password in the output"
          ],
          image:
            "https://images.unsplash.com/photo-1517545084371-4a575dde2a02?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=934&q=80"
        },
        {
          title: "⚠️ (3) secret data leaked by logs",
          description: [
            "Environment variables are often times erroneously used as metadata added to error logging which ends up in logs or other print-out that risks providing this information to unauthorised users.",
            "To serve as a practical reference for such security issues, I'll refer you to <a href='https://snyk.io/vuln/SNYK-JS-SENECA-460597'>CVE-2019-5483</a> - an information exposure vulnerability in the form of environment variables leaking secrets, such as cloud API keys in one referrenced incident, that was found in the Node.js microservices toolkit called <a href='https://www.npmjs.com/package/seneca'>seneca</a>.",
            "When applications crash, a common practice is to provide rich debug information in the form of a stack trace, environment variables and more. This becomes another source of data leakage."
          ],
          image:
            "https://images.unsplash.com/photo-1512581574034-6f1da619c5fa?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1931&q=80"
        },
        {
          title: "⚠️ (4) Build arguments leak into docker images",
          description: [
            "Environment variables get leaked in docker image history and leave traces of the build arguments used across directives in layers as well as the build arguments provided to build the image.",
            "For example, if the <code>Dockerfile</code> expects a build-time argument such as <code>ARG MY_SECRET</code>, which gets passed via <code>docker build . --build MY_SECRET=1234</code>, then that secret shows up on <code>docker history [image-name]</code>",
            "How bad are information exposure vulnerabilities for Docker? <a href='https://www.intrinsec.com/docker-leak/'>10% of images on Docker Hub are leaking sensitive data</a>.",
            "There are however, more secure ways to build docker images, such as using mutli-stage docker image."
          ],
          image:
            "https://images.unsplash.com/photo-1577401089489-93b743840737?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=500&q=60"
        }
      ]
    };
  }
};
</script>