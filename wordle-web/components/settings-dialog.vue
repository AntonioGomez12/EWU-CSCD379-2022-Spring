<template>
  <div>

     <v-btn icon @click="helpDialog">
      <v-icon> mdi-help </v-icon>
    </v-btn>

    <v-btn icon nuxt to="/leaderboard">
      <v-icon>mdi-podium-gold</v-icon>
    </v-btn>

    <v-btn icon @click="aboutDialog">
      <v-icon> mdi-hamburger</v-icon>
    </v-btn>

    <v-btn icon @click="toggleDialog">
      <v-icon> mdi-cog </v-icon>
    </v-btn>

   

     <v-dialog v-model="about" width="450">
      <v-card>
        <v-container>
          <v-card-title> Menu </v-card-title>

          <v-card-text>
            <v-menu offset-y>
              <template #activator="{ on, attrs }">
                <v-btn color="primary" dark v-bind="attrs" nuxt to="/about" v-on="on" >
                  About
                </v-btn>
              </template>
            </v-menu>

           
          </v-card-text>

          <v-card-text>
            <v-menu offset-y>
              <template #activator="{ on, attrs }">
                <v-btn color="primary" dark v-bind="attrs" @click="helpDialog" v-on="on" >
                  How to play
                </v-btn>
              </template>
            </v-menu>

           
          </v-card-text>
        </v-container>
      </v-card>
    </v-dialog>

         <v-dialog v-model="help" width="450">
      <v-card>
        <v-container>
          <v-card-title> Help </v-card-title>

          <v-card-text>
            <v-menu offset-y>
              <template #activator="{ on, attrs }">
                <br>
                <br>
                <v-btn color="success" dark v-bind="attrs" v-on="on">
                  Letter is part of word<br>
                  (right spot)
                </v-btn>
                <br>
                <br>
                <v-btn color="warning" dark v-bind="attrs" v-on="on">
                  Letter is part of word<br>
                  (wrong spot)
                </v-btn>
                <br>
                <br>
                <v-btn color="error" dark v-bind="attrs" v-on="on">
                  Letter is not part of word<br>
                  (Wrong letter choice)
                </v-btn>

                <p>
                Guess the word of the day! Use the letter keys to stage a word, then press the
                Guess key to see how close your guess is!  
                You get 6 tries then its GAME OVER!
                Use key ? to fill in word space and then click the red fill
                button (cheat) to generate a list of possible words!
                GOODLUCK!
                </p>
              </template>
            </v-menu>

           
          </v-card-text>
        </v-container>
      </v-card>
    </v-dialog>
    

    

    

  

    <v-dialog v-model="dialog" width="450">
      <v-card>
        <v-container>
          <v-card-title> Settings </v-card-title>

          <v-card-text>
            <v-menu offset-y>
              <template #activator="{ on, attrs }">
                <v-btn color="primary" dark v-bind="attrs" v-on="on">
                  Pick Theme
                </v-btn>
              </template>
              <v-list>
                <v-list-item-group>
                  <v-list-item @click="turnOnTheLights">
                    <v-list-item-title> Light Mode </v-list-item-title>
                  </v-list-item>
                  <v-list-item @click="turnOffTheLights">
                    <v-list-item-title> Dark Mode </v-list-item-title>
                  </v-list-item>
                </v-list-item-group>
              </v-list>
            </v-menu>

            <v-menu offset-y>
              <template #activator="{ on, attrs }">
                <v-btn color="primary" dark v-bind="attrs" v-on="on">
                  Pick A Color
                </v-btn>
              </template>
              <v-list>
                <v-list-item-group>
                  <v-list-item @click="purpleTheme">
                    <v-list-item-title> Purple </v-list-item-title>
                  </v-list-item>
                  <v-list-item @click="vampireTheme">
                    <v-list-item-title> vampire </v-list-item-title>
                  </v-list-item>
                  <v-list-item @click="spaceTheme">
                    <v-list-item-title> space race </v-list-item-title>
                  </v-list-item>
                </v-list-item-group>
              </v-list>
            </v-menu>

            
          </v-card-text>
        </v-container>
      </v-card>
    </v-dialog>
  </div>

  




  
</template>



<script lang="ts">
import { Vue, Component } from 'vue-property-decorator'
import { colors } from 'vuetify/lib'

@Component({})
export default class SettingsDialog extends Vue {
  dialog = false
  about = false
  help = false

  toggleDialog() {
    this.dialog = !this.dialog
  }

  aboutDialog(){
    this.about = !this.about
  }

  helpDialog(){
    this.help = !this.help
  }

  turnOnTheLights() {
    this.$vuetify.theme.dark = false
  }

  turnOffTheLights() {
    // Implement Me
    this.$vuetify.theme.dark = true
  }

  purpleTheme() {
    const purpleTheme = {
      primary: colors.deepPurple,
      accent: colors.purple.accent3,
      secondary: colors.purple,
      info: '#03A9F4',
      warning: colors.pink.accent1,
      error: colors.pink.accent3,
      success: colors.deepPurple.lighten4,
    }
    

    this.$vuetify.theme.themes.dark = purpleTheme
    this.$vuetify.theme.themes.light = purpleTheme
  }
  
    vampireTheme() {
    const vampireTheme = {
      primary: colors.red,
      accent: colors.red.darken3,
      secondary: colors.red,
      info: '#C62828',
      warning: '#827717',
      error:  '#880E4F',
      success: '#B2DFDB',
    }
    

    this.$vuetify.theme.themes.dark = vampireTheme
    this.$vuetify.theme.themes.light = vampireTheme
  }
  
    spaceTheme() {
    const spaceTheme = {
      primary: '#18FFFF',
      accent: '#18FFFF',
      secondary: '#18FFFF',
      info: '#18FFFF',
      warning: '#FFA000',
      error:  '#651FFF',
      success: '#76FF03',
    }
    

    this.$vuetify.theme.themes.dark = spaceTheme
    this.$vuetify.theme.themes.light = spaceTheme
  }
}
</script>
