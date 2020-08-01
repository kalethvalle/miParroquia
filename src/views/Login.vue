<template>
  <v-container fluid mt-0 pa-0 fill-height>
    <v-layout row>
      <v-col md="6">
        <v-container class="ma-5 pa-5">
          <v-card max-width="500" class="mx-auto" style="padding: 30px;" elevation="9">
            <v-card-title class="display-1 text--primary">Iniciar Sesión</v-card-title>
            <v-card-subtitle class="mt-1">Ingrese su dirección de correo electrónico y contraseña para acceder al panel de administración.</v-card-subtitle>
            <v-card-text>
              <v-row class="d-flex">
                <v-col cols="12" md="12">
                  <v-text-field v-model="email" label="E-mail" required></v-text-field>
                </v-col>
                <v-col cols="12" md="12">
                  <v-text-field v-model="clave" label="Password" type="password" required></v-text-field>
                </v-col>
              </v-row>
            </v-card-text>

            <v-card-actions>
              <v-checkbox label="Recordar contraseña?" required></v-checkbox>
              <v-spacer></v-spacer>
              <v-btn class="text-capitalize" color="indigo" dark @click="login">Sign in</v-btn>
            </v-card-actions>
            <v-divider></v-divider>
            <div class="pa-5">
              <v-row class="d-flex">
                <v-col cols="7">
                  <p>
                    ¿No tienes una cuenta?
                    <a href="#">Sign up</a>
                  </p>
                </v-col>
                <v-spacer></v-spacer>
                <v-col cols="4">
                  <v-btn icon x-small>
                    <v-icon color="indigo">mdi-facebook</v-icon>
                  </v-btn>
                  <v-btn icon x-small>
                    <v-icon color="indigo">mdi-google</v-icon>
                  </v-btn>
                </v-col>
              </v-row>
            </div>
          </v-card>
        </v-container>
      </v-col>
      <v-col md="6" >
        <v-carousel cycle height="700" hide-delimiter-background :show-arrows="false" class="ml-0">
          <v-carousel-item v-for="(slide, i) in slides" :key="i">
            <v-sheet :color="colors[i]" height="100%">
              <v-row class="fill-height" align="center" justify="center">
                <div class="display-3">{{ slide }} Slide</div>
              </v-row>
            </v-sheet>
          </v-carousel-item>
        </v-carousel>
      </v-col>
    </v-layout>
  </v-container>
</template>
<script>
import axios from "axios";
export default {
  data() {
    return {
      email: "",
      clave: "",
      colors: ["indigo", "warning", "pink darken-2"],
      slides: ["First", "Second", "Third"]
    };
  },
  methods: {
    login() {
      const users = {
        email: this.email,
        password: this.clave
      };

      axios
        .post("34.239.143.53/api/auth/login", {
          email: this.email,
          password: this.clave
        })
        .then(response => {
          console.log(response);
        })
        .catch(e => {
          console.log(e);
        });
    }
  }
};
</script>