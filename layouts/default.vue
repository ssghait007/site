<template>
  <div>
    <v-app dark v-if="loaded">
      <v-navigation-drawer
        v-model="drawer"
        :mini-variant="miniVariant"
        :clipped="clipped"
        fixed
        app
      >
        <v-list>
          <v-list-item
            v-for="(item, i) in items"
            :key="i"
            :to="item.to"
            router
            exact
          >
            <v-list-item-action>
              <v-icon>{{ item.icon }}</v-icon>
            </v-list-item-action>
            <v-list-item-content>
              <v-list-item-title v-text="item.title" />
            </v-list-item-content>
          </v-list-item>
        </v-list>
      </v-navigation-drawer>
      <v-app-bar :clipped-left="clipped" fixed app>
        <v-app-bar-nav-icon @click.stop="drawer = !drawer" />
        <v-btn icon @click.stop="miniVariant = !miniVariant">
          <v-icon>mdi-{{ `chevron-${miniVariant ? 'right' : 'left'}` }}</v-icon>
        </v-btn>
        <v-btn icon @click.stop="clipped = !clipped">
          <v-icon>mdi-application</v-icon>
        </v-btn>
        <!-- <v-btn icon @click.stop="fixed = !fixed">
        <v-icon>mdi-minus</v-icon>
      </v-btn> -->
        <v-toolbar-title v-text="title" />
        <v-spacer />
      </v-app-bar>
      <v-main>
        <v-container>
          <nuxt />
        </v-container>
      </v-main>

      <v-footer :absolute="!fixed" app>
        <span
          >&copy; {{ new Date().getFullYear() }} Author: Sachin Ghait
          <a href="mailto:ssghait.007@gmail.com">ssghait.007@gmail.com</a>
        </span>
      </v-footer>
    </v-app>
    <div
      v-else
      class="square-group"
      xyz="tall-2 duration-6 ease-out-back stagger-1 skew-left-2 big-25% fade-100% right-5"
    >
      <div class="square xyz-in"></div>
      <div class="square xyz-in"></div>
      <div class="square xyz-in"></div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      clipped: true,
      drawer: false,
      fixed: true,
      items: [
        {
          icon: 'mdi-home',
          title: 'Home',
          to: '/',
        },
        {
          icon: 'mdi-dialpad',
          title: 'WorK Experience',
          to: '/projects',
        },
        {
          icon: 'mdi-face',
          title: 'About me',
          to: '/aboutme',
        },
        {
          icon: 'mdi-email',
          title: 'Contact',
          to: '/contact',
        },
      ],
      miniVariant: false,
      title: 'Sachin Ghait',
      loaded: false,
    }
  },
  mounted() {
    const $this = this

    const squares = document.querySelectorAll('.square')
    const animateSquares = setInterval(() => {
      squares.forEach((square) => {
        square.classList.toggle('xyz-in')
        square.classList.toggle('xyz-out')
      })
    }, 1200)

    window.addEventListener('load', function () {
      clearInterval(animateSquares)
      $this.loaded = true
    })
  },
}
</script>
<style lang="scss">
@import '@animxyz/core';
@include xyz-all;
.square-group {
  display: flex;
  gap: 1rem;
  align-items: center;
  justify-content: center;
  height: 100vh;
}
.square {
  background: #57cbf2;
  width: 4vw;
  height: 4vw;
}
</style>
