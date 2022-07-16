<template>
  <section id="download">
    <v-container fluid>
      <v-row align="center" justify="center">
        <v-col cols="10">
          <v-row align="center" justify="center">
            <v-col sm="4" class="hidden-xs-only">
              <v-img
                src="@/assets/img/ill2.svg"
                class="d-block ml-auto mr-auto"
                max-width="350px"
              />
            </v-col>
            <v-col cols="12" sm="8" class="white--text text-left">
              <h1 class="font-weight-light display-2 mb-2">Galeria</h1>
              <h1 class="font-weight-light">
                Lorem ipsum dolor sit amet consectetur adipisicing elit. Iste ex
                animi quod laboriosam vel blanditiis labore alias, aliquid,
                tempora repellendus non.
              </h1>

              <v-dialog v-model="dialog" width="700">
                <template v-slot:activator="{ on, attrs }">
                  <v-btn
                    rounded
                    outlined
                    large
                    color="white"
                    class="mt-4"
                    dark
                    v-bind="attrs"
                    v-on="on"
                  >
                    <v-icon class="mr-2"> mdi-arrow-down </v-icon>
                    Abrir Galeria
                  </v-btn>
                </template>

                <v-card>
                  <v-carousel v-model="model">
                    <v-carousel-item>
                      <v-sheet height="100%" tile>
                        <v-row
                          class="fill-height"
                          align="center"
                          justify="center"
                        >
                          <img
                            src="../assets/img/render1.jpeg"
                            width="100%"
                            alt="image"
                          />
                        </v-row>
                      </v-sheet>
                    </v-carousel-item>
                    <v-carousel-item>
                      <v-sheet height="100%" tile>
                        <v-row
                          class="fill-height"
                          align="center"
                          justify="center"
                        >
                          <img
                            src="../assets/img/render2.jpeg"
                            width="100%"
                            alt="image"
                          />
                        </v-row>
                      </v-sheet>
                    </v-carousel-item>
                    <v-carousel-item>
                      <v-sheet height="100%" tile>
                        <v-row
                          class="fill-height"
                          align="center"
                          justify="center"
                        >
                          <img
                            src="../assets/img/render3.jpeg"
                            width="100%"
                            alt="image"
                          />
                        </v-row>
                      </v-sheet>
                    </v-carousel-item>
                    <v-carousel-item>
                      <v-sheet height="100%" tile>
                        <v-row
                          class="fill-height"
                          align="center"
                          justify="center"
                        >
                          <img
                            src="../assets/img/render4.jpeg"
                            width="100%"
                            alt="image"
                          />
                        </v-row>
                      </v-sheet>
                    </v-carousel-item>
                  </v-carousel>
                </v-card>
              </v-dialog>
            </v-col>
          </v-row>
        </v-col>
      </v-row>
    </v-container>
  </section>
</template>

<script>
export default {
  data: () => ({
    model: 0,
    dialog: false,
    images: [
      { src: "../assets/img/render1.jpeg" },
      { src: "../assets/img/render2.jpeg" },
      { src: "../assets/img/render3.jpeg" },
      { src: "../assets/img/render4.jpeg" },
    ],
  }),
  methods: {
    handleDialog() {
      dialog = !dialog;
    },
  },
};
</script>
<style scoped>
#download {
  background-image: url("~@/assets/img/bgDownload.jpg");
  background-attachment: fixed;
  background-repeat: no-repeat;
  background-size: cover;
  background-position: center;
  height: 500px;
}

#download .container,
#download .row {
  height: 100%;
}
</style>