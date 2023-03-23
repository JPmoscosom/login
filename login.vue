<template>
  <v-container class="fill-height" fluid>
    <v-row align="center" justify="center">
      <v-col cols="12" sm="8" md="8">
        <v-card class="elevation-12 rounded">
          <v-row>
            <v-col cols="12" md="8">
              <v-card-title class="justify-center mt-4">
                <h4
                  class="text-center display-1 deep-purple--text text-darken-1"
                >
                  {{ title }}
                </h4>
              </v-card-title>
              <v-card-text class="mt-8">
                <div class="text-center mt-4">
                  <v-btn class="mx-2" color="black" outlined>
                    <v-icon>mdi-facebook</v-icon>
                  </v-btn>

                  <v-btn class="mx-2" color="black" outlined>
                    <v-icon>mdi-google</v-icon>
                  </v-btn>
                  <v-btn class="mx-2" color="black" outlined>
                    <v-icon>mdi-linkedin</v-icon>
                  </v-btn>
                </div>
                <h4 class="text-center mt-5">
                  {{ emailOption }}
                </h4>
                <v-form class="mt-3 mx-4">
                  <v-text-field
                    label="Email"
                    name="Email"
                    prepend-icon="mdi-email"
                    type="text"
                    color="deep-purple accent-3"
                    :rules="[rules.required, ...emailRules]"
                    v-model="account.email"
                    required
                    class="form-input"
                  />

                  <v-text-field
                    id="password"
                    label="Contraseña"
                    name="password"
                    prepend-icon="mdi-lock"
                    color="deep-purple accent-3"
                    :rules="[rules.required]"
                    :type="showPassword ? 'text' : 'password'"
                    required
                    :append-icon="showPassword ? 'mdi-eye-off' : 'mdi-eye'"
                    @click:append="changeVisibilityPassword"
                    class="form-input"
                  />
                </v-form>
                <h3 class="text-center mt-4">{{ forgotPass }}</h3>
              </v-card-text>
              <div class="text-center mt-3">
                <v-btn radius="10px" color="deep-purple accent-3" dark
                  >Entrar</v-btn
                >
              </div>
            </v-col>
            <v-col cols="12" md="4" class="deep-purple accent-3 rounded">
              <v-card-text class="white--text mt-4">
                <h1 class="text-center display-1">{{ saludo }}</h1>
                <h5 class="text-center mt-12">{{ mensaje }}</h5>
              </v-card-text>
              <div class="text-center mt-15">
                <v-btn @click="goToRegister" radius="10px" outlined dark
                  >Registrarse</v-btn
                >
              </div>
            </v-col>
          </v-row>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script lang="ts">
export default {
  data() {
    return {
      showPassword: false,
      title: 'Login',
      emailOption: 'Tambien puedes ingresar con tu email',
      forgotPass: '¿Olvidaste tu contraseña?',
      saludo: 'Holiwis!',
      mensaje:
        'Si no estas registrado, haz click el boton de abajo y disfruta de nuestros servicios!',
      account: {
        email: '',
        pass: '',
      },
      // Reglas generales
      rules: {
        required: (v: String | null) => !!v || 'Este campo es obligatorio.',
      },
      //Reglas especificas
      emailRules: [
        (v: string) => /.+@.+\..+/.test(v) || 'El correo debe ser valido',
      ],
    }
  },
  methods: {
    goToRegister() {
      this.$router.push('/register')
    },
    changeVisibilityPassword() {
      this.showPassword = !this.showPassword
      console.log(this.showPassword)
    },
  },
}
</script>

<style>
.form-input.error--text,
.form-input .error--text {
  color: rgb(135, 7, 255) !important;
  caret-color: rgb(135, 7, 255) !important;
}
</style>
