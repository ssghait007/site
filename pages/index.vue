<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="8" md="6" xs="4">
      <div class="text-center pa-10">
        <div
          :class="[`text-h1`, `mb--1`, `font-weight-bold`]"
          class="transition-swing"
          v-text="'Hi,'"
        ></div>
        <img
          src="https://raw.githubusercontent.com/MartinHeinz/MartinHeinz/master/wave.gif"
          width="30px"
        />
        <div
          :class="[`text-h2`, `mb--1`, `font-weight-bold`]"
          class="transition-swing"
          v-text="`I'm Sachin Ghait`"
        ></div>
        <div
          :class="[`text-caption`, `mb--1`, `font-weight-bold`]"
          class="transition-swing"
          v-text="`Full-stack Software Engineer | Web developer`"
        ></div>
      </div>
      <div class="pa-10">
        <v-divider></v-divider>
      </div>
      <div class="text-center pa-10">
        <v-btn elevation="2" large outlined x-large to="/aboutme">
          About me
        </v-btn>
      </div>
    </v-col>
  </v-row>
</template>

<script>
export default {}
</script>
