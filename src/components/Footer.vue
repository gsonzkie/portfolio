<template>
  <v-footer dark padless :app="true" fixed class="flex">
    <v-card flat tile>
      <v-card-subtitle>
        <v-spacer></v-spacer>
        <vs-switch color="dark" v-model="bg" @click="toggleMode()" />
        <v-btn v-for="icon in icons" :key="icon.index" class="mx-4" icon>
          <!-- https://bolajiayodeji.com/the-security-vulnerabilities-of-the-target_blank-attribute-cka3hgvyw01axdjs13r1xgc7m -->
          <a :href="icon.link" target="_blank" rel="noopener noreferrer">
            <v-icon size="30px" color="red">{{ icon.image }}</v-icon>
          </a>
        </v-btn>
      </v-card-subtitle>
    </v-card>
  </v-footer>
</template>

<script>
export default {
  data: () => ({
    icons: [
      { image: "fab fa-github", link: "https://github.com/gsonzkie" },
      {
        image: "fab fa-linkedin",
        link: "https://www.linkedin.com/in/jasonperu0608"
      },
      {
        image: "fa fa-envelope",
        link: "mailto: gsonzkie12@gmail.com"
      }
    ]
  }),
  methods: {
    toggleMode() {
      if (this.bg) {
        document.documentElement.setAttribute("data-theme", "dark");
        this.bg.set;
      } else {
        document.documentElement.setAttribute("data-theme", "light");
        this.bg.set;
      }
    }
  },
  computed: {
    bg: {
      get() {
        const bg = this.$store.state.dark;
        return bg;
      },
      set() {
        this.$store.commit("mode");
      }
    }
  }
};
</script>

<style scoped>
.v-footer {
  width: 0vw;
  max-height: 20vh;
  margin-bottom: 1vh;
}

.v-card__subtitle {
  background-color: var(--bg-color);
  padding: 10px 0px 10px 0px !important;
}

.v-btn--icon {
  color: var(--content-color) !important;
}

a {
  color: inherit;
}
</style>
