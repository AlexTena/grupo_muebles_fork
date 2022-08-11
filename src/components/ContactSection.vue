<template>
  <section class="pb-8" id="contact">
    <v-container fluid>
      <v-row align="center" justify="center">
        <v-col cols="10">
          <v-row justify="center">
            <v-col cols="12" sm="5">
              <h1 class="font-weight-light display-1">Contacto</h1>
              <h3 class="font-weight-light mt-3"></h3>
              <h3 class="font-weight-light mt-3">
                Ponte en contacto con nosotros.
              </h3>
              <h3 class="font-weight-light mt-3">Telefono: 33 38 52 57 05</h3>
              <h3 class="font-weight-light">
                Email: ventas@grupoocamuebles.com
              </h3>
              <div class="text-start mt-4">
                <iframe
                  src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d554.0582623864944!2d-103.45293767532758!3d20.66299644292079!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x8428a954a1dc168b%3A0x7ba8c77c2ee7e18!2sP.%C2%BA%20de%20Las%20Lomas%20B13%2C%20Lomas%20del%20Colli%2C%2045010%20Zapopan%2C%20Jal.!5e0!3m2!1ses-419!2smx!4v1654738927082!5m2!1ses-419!2smx"
                  width="90%"
                  height="100%"
                  style="border: 0"
                  allowfullscreen=""
                  loading="lazy"
                  referrerpolicy="no-referrer-when-downgrade"
                ></iframe>
              </div>
            </v-col>
            <v-col cols="12" sm="7">
              <v-form ref="form" v-model="valid" :lazy-validation="lazy">
                <v-text-field
                  v-model="name"
                  :rules="nameRules"
                  label="Nombre"
                  required
                ></v-text-field>

                <v-text-field
                  v-model="email"
                  :rules="emailRules"
                  label="E-mail"
                  required
                ></v-text-field>

                <v-textarea
                  v-model="message"
                  :rules="textAreaRules"
                  label="Comentarios"
                  required
                />

                <v-btn
                  :disabled="!valid"
                  color="primary"
                  :dark="valid"
                  rounded
                  block
                  class="mt-3"
                  @click="submit"
                >
                  Enviar
                </v-btn>
              </v-form>
            </v-col>
          </v-row>
        </v-col>
      </v-row>
    </v-container>
    <div class="svg-border-waves text-white">
      <v-img src="~@/assets/img/borderWavesBlue.svg" />
    </div>
    <v-snackbar
      v-model="snackbar.enabled"
      timeout="3000"
      right
      top
      :color="snackbar.color"
    >
      {{ snackbar.text }}

      <template v-slot:action="{ attrs }">
        <v-btn text v-bind="attrs" @click="snackbar.enabled = false">
          Fecha
        </v-btn>
      </template>
    </v-snackbar>
  </section>
</template>

<style scoped>
#contact {
  background-color: #f4f7f5;
}

.svg-border-waves .v-image {
  position: absolute;
  bottom: 0;
  left: 0;
  height: 3rem;
  width: 100%;
  overflow: hidden;
}
</style>

<script>
import emailjs from "emailjs-com";

export default {
  data: () => ({
    icons: ["fa-facebook", "fa-twitter", "fa-linkedin", "fa-instagram"],
    valid: true,
    name: "",
    nameRules: [
      (v) => !!v || "El campo de nombre es obligatorio",
      (v) => (v && v.length >= 5) || "El nombre debe tener más de 5 caracteres",
    ],
    email: "",
    emailRules: [
      (v) => !!v || "El campo de email es obligatorio",
      (v) => /.+@.+\..+/.test(v) || "Debe ser un email valido",
    ],
    message: "",
    textAreaRules: [
      (v) => !!v || "El campo de comentarios es obligatorio",
      (v) => (v && v.length >= 10) || "Minimo 10 caracteres",
    ],
    lazy: false,
    snackbar: {
      enabled: false,
      text: "",
      color: "",
    },
  }),
  methods: {
    submit() {
      try {
        emailjs.send(
          "service_1ip58pm",
          "template_0lbnfvn",

          {
            name: this.name,
            email: this.email,
            message: this.message,
          },
          "-xtlfdVG5rrKufZ6A"
        );

        this.snackbar.text = "Mensaje enviado con éxito";
        this.snackbar.color = "success";
        this.snackbar.enabled = true;
      } catch (error) {
        console.log(error);
        this.snackbar.text = "Error al enviar mensaje";
        this.snackbar.color = "danger";
        this.snackbar.enabled = true;
      }

      this.$refs.form.reset();
    },
  },
};
</script>
