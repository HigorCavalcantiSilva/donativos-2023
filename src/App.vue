<template>
  <v-app>
    <v-app-bar app color="primary" dark>
      <h1>Donativos</h1>

      <v-spacer></v-spacer>

      <v-btn              
        color="error"
        elevation="2"
        @click="confirmarResetar"
      >RESETAR</v-btn>
    </v-app-bar>

    <v-main>
      <v-tabs>
        <v-tab> CÉDULAS </v-tab>
        <v-tab> MOEDAS </v-tab>
        <v-tab> TOTAIS </v-tab>

        <v-tab-item>
          <v-card flat>
            <v-form>
              <v-container>
                <v-row>
                  <v-col cols="6" md="4">
                    <v-text-field
                      v-model="reais_2"
                      label="Qtd. R$ 2,00"
                      @input="calcularValores"
                      type="number"
                    ></v-text-field>
                  </v-col>

                  <v-col cols="6" md="4">
                    <v-text-field
                      v-model="reais_5"
                      label="Qtd. R$ 5,00"
                      @input="calcularValores"
                      type="number"
                    ></v-text-field>
                  </v-col>

                  <v-col cols="6" md="4">
                    <v-text-field
                      v-model="reais_10"
                      label="Qtd. R$ 10,00"
                      @input="calcularValores"
                      type="number"
                    ></v-text-field>
                  </v-col>
                  <v-col cols="6" md="4">
                    <v-text-field
                      v-model="reais_20"
                      label="Qtd. R$ 20,00"
                      @input="calcularValores"
                      type="number"
                    ></v-text-field>
                  </v-col>

                  <v-col cols="6" md="4">
                    <v-text-field
                      v-model="reais_50"
                      label="Qtd. R$ 50,00"
                      @input="calcularValores"
                      type="number"
                    ></v-text-field>
                  </v-col>

                  <v-col cols="6" md="4">
                    <v-text-field
                      v-model="reais_100"
                      label="Qtd. R$ 100,00"
                      @input="calcularValores"
                      type="number"
                    ></v-text-field>
                  </v-col>
                </v-row>
              </v-container>
            </v-form>
            <v-card
              class="mx-auto"
              max-width="344"
              outlined
            >
              <v-card-title> <v-spacer></v-spacer> Total de Cédulas: {{ total_cedulas }}</v-card-title>
            </v-card>
          </v-card>
        </v-tab-item>
        <v-tab-item>
          <v-card flat>
            <v-form>
              <v-container>
                <v-row>
                  <v-col cols="6" md="4">
                    <v-text-field
                      v-model="reais_001"
                      label="Qtd. R$ 0,01"
                      @input="calcularValores"
                      type="number"
                    ></v-text-field>
                  </v-col>

                  <v-col cols="6" md="4">
                    <v-text-field
                      v-model="reais_005"
                      label="Qtd. R$ 0,05"
                      @input="calcularValores"
                      type="number"
                    ></v-text-field>
                  </v-col>

                  <v-col cols="6" md="4">
                    <v-text-field
                      v-model="reais_010"
                      label="Qtd. R$ 0,10"
                      @input="calcularValores"
                      type="number"
                    ></v-text-field>
                  </v-col>
                  <v-col cols="6" md="4">
                    <v-text-field
                      v-model="reais_025"
                      label="Qtd. R$ 0,25"
                      @input="calcularValores"
                      type="number"
                    ></v-text-field>
                  </v-col>

                  <v-col cols="6" md="4">
                    <v-text-field
                      v-model="reais_050"
                      label="Qtd. R$ 0,50"
                      @input="calcularValores"
                      type="number"
                    ></v-text-field>
                  </v-col>

                  <v-col cols="6" md="4">
                    <v-text-field
                      v-model="reais_1"
                      label="Qtd. R$ 1,00"
                      @input="calcularValores"
                      type="number"
                    ></v-text-field>
                  </v-col>
                </v-row>
              </v-container>
            </v-form>
            <v-card
              class="mx-auto"
              max-width="344"
              outlined
            >
              <v-card-title> <v-spacer></v-spacer> Total de Moedas: {{ total_moedas }}</v-card-title>
            </v-card>
          </v-card>
        </v-tab-item>
        <v-tab-item>
          <v-card flat>
            <v-expansion-panels multiple>
              <v-expansion-panel>
                <v-expansion-panel-header>
                  <h3>Total de Cédulas:</h3> <v-spacer></v-spacer> <h3 class="blue--text">{{ total_cedulas }}</h3>
                </v-expansion-panel-header>
                <v-expansion-panel-content>
                  <v-row>
                    <v-col cols="12" md="3">
                      <v-list-item>
                        <v-list-item-content>
                          <v-list-item-title>R$ 2,00 ({{ reais_2 || 0 }}): <b>{{ (reais_2 * 2).toLocaleString('pt-BR', { style: 'currency', currency: 'BRL'}) }}</b></v-list-item-title>
                        </v-list-item-content>
                      </v-list-item>
                    </v-col>
                    <v-col cols="12" md="3">
                      <v-list-item>
                        <v-list-item-content>
                          <v-list-item-title>R$ 5,00 ({{ reais_5 || 0 }}): <b>{{ (reais_5 * 5).toLocaleString('pt-BR', { style: 'currency', currency: 'BRL'}) }}</b></v-list-item-title>
                        </v-list-item-content>
                      </v-list-item>
                    </v-col>
                    <v-col cols="12" md="3">
                      <v-list-item>
                        <v-list-item-content>
                          <v-list-item-title>R$ 10,00 ({{ reais_10 || 0 }}): <b>{{ (reais_10 * 10).toLocaleString('pt-BR', { style: 'currency', currency: 'BRL'}) }}</b></v-list-item-title>
                        </v-list-item-content>
                      </v-list-item>
                    </v-col>
                    <v-col cols="12" md="3">
                      <v-list-item>
                        <v-list-item-content>
                          <v-list-item-title>R$ 20,00 ({{ reais_20 || 0 }}): <b>{{ (reais_20 * 20).toLocaleString('pt-BR', { style: 'currency', currency: 'BRL'}) }}</b></v-list-item-title>
                        </v-list-item-content>
                      </v-list-item>
                    </v-col>
                    <v-col cols="12" md="3">
                      <v-list-item>
                        <v-list-item-content>
                          <v-list-item-title>R$ 50,00 ({{ reais_50 || 0 }}): <b>{{ (reais_50 * 50).toLocaleString('pt-BR', { style: 'currency', currency: 'BRL'}) }}</b></v-list-item-title>
                        </v-list-item-content>
                      </v-list-item>
                    </v-col>
                    <v-col cols="12" md="3">
                      <v-list-item>
                        <v-list-item-content>
                          <v-list-item-title>R$ 100,00 ({{ reais_100 || 0 }}): <b>{{ (reais_100 * 100).toLocaleString('pt-BR', { style: 'currency', currency: 'BRL'}) }}</b></v-list-item-title>
                        </v-list-item-content>
                      </v-list-item>
                    </v-col>
                  </v-row>
                </v-expansion-panel-content>
              </v-expansion-panel>
              <v-expansion-panel>
                <v-expansion-panel-header>
                  <h3>Total de Moedas:</h3> <v-spacer></v-spacer> <h3 class="blue--text">{{ total_moedas }}</h3>
                </v-expansion-panel-header>
                <v-expansion-panel-content>
                  <v-row>
                    <v-col cols="12" md="3">
                      <v-list-item>
                        <v-list-item-content>
                          <v-list-item-title>R$ 0,01 ({{ reais_001 || 0 }}): <b>{{ (reais_001 * 0.01).toLocaleString('pt-BR', { style: 'currency', currency: 'BRL'}) }}</b></v-list-item-title>
                        </v-list-item-content>
                      </v-list-item>
                    </v-col>
                    <v-col cols="12" md="3">
                      <v-list-item>
                        <v-list-item-content>
                          <v-list-item-title>R$ 0,05 ({{ reais_005 || 0 }}): <b>{{ (reais_005 * 0.05).toLocaleString('pt-BR', { style: 'currency', currency: 'BRL'}) }}</b></v-list-item-title>
                        </v-list-item-content>
                      </v-list-item>
                    </v-col>
                    <v-col cols="12" md="3">
                      <v-list-item>
                        <v-list-item-content>
                          <v-list-item-title>R$ 0,10 ({{ reais_010 || 0 }}): <b>{{ (reais_010 * 0.1).toLocaleString('pt-BR', { style: 'currency', currency: 'BRL'}) }}</b></v-list-item-title>
                        </v-list-item-content>
                      </v-list-item>
                    </v-col>
                    <v-col cols="12" md="3">
                      <v-list-item>
                        <v-list-item-content>
                          <v-list-item-title>R$ 0,25 ({{ reais_025 || 0 }}): <b>{{ (reais_025 * 0.25).toLocaleString('pt-BR', { style: 'currency', currency: 'BRL'}) }}</b></v-list-item-title>
                        </v-list-item-content>
                      </v-list-item>
                    </v-col>
                    <v-col cols="12" md="3">
                      <v-list-item>
                        <v-list-item-content>
                          <v-list-item-title>R$ 0,50 ({{ reais_050 || 0 }}): <b>{{ (reais_050 * 0.5).toLocaleString('pt-BR', { style: 'currency', currency: 'BRL'}) }}</b></v-list-item-title>
                        </v-list-item-content>
                      </v-list-item>
                    </v-col>
                    <v-col cols="12" md="3">
                      <v-list-item>
                        <v-list-item-content>
                          <v-list-item-title>R$ 1,00 ({{ reais_1 || 0 }}): <b>{{ (reais_1 * 1).toLocaleString('pt-BR', { style: 'currency', currency: 'BRL'}) }}</b></v-list-item-title>
                        </v-list-item-content>
                      </v-list-item>
                    </v-col>
                  </v-row>
                </v-expansion-panel-content>
              </v-expansion-panel>
            </v-expansion-panels>
            <v-card
              width="100%"
              outlined
            >
              <v-card-title class="green--text">Total Geral: <v-spacer></v-spacer> {{ total_geral }}</v-card-title>
            </v-card>
          </v-card>
        </v-tab-item>
      </v-tabs>
      <v-row justify="center">
        <v-dialog
          v-model="dialog"
          persistent
          max-width="290"
        >
          <v-card>
            <v-card-title class="text-h5">
              Deseja resetar todos os dados?
            </v-card-title>
            <v-card-text>A quantidade de cada campo será limpa e os totais voltarão a ser R$ 0,00.</v-card-text>
            <v-card-actions>
              <v-spacer></v-spacer>
              <v-btn
                color="red darken-1"
                text
                @click="dialog = false"
              >
                Cancelar
              </v-btn>
              <v-btn
                color="green darken-1"
                text
                @click="limparLocalStorage"
              >
                Confirmar
              </v-btn>
            </v-card-actions>
          </v-card>
        </v-dialog>
      </v-row>
      <v-footer width="100%" padless style="position: absolute; bottom: 0;">
        <v-col
          class="text-center"
        >
          Desenvolvido por: Higor Cavalcanti
        </v-col>
      </v-footer>
    </v-main>
  </v-app>
</template>

<script>
export default {
  name: "App",
  mounted: function() {
    this.inicializar()
  },
  data: () => ({
    //
    items: ["Cedulas", "Moedas", "Totais"],
    dialog: false,
    total_cedulas: 0,
    total_moedas: 0,
    total_geral: 0,
    reais_2: "",
    reais_5: "",
    reais_10: "",
    reais_20: "",
    reais_50: "",
    reais_100: "",
    reais_001: "",
    reais_005: "",
    reais_010: "",
    reais_025: "",
    reais_050: "",
    reais_1: ""
  }),
  
  methods: {
    inicializar(resetar = false) {
      this.buscarValoresLocalStorage(resetar);
      this.calcularValores();
    },

    calcularValores() {
      this.total_cedulas = this.calcularCedulas().toLocaleString('pt-BR', { style: 'currency', currency: 'BRL'});
      this.total_moedas = this.calcularMoedas().toLocaleString('pt-BR', { style: 'currency', currency: 'BRL'});
      this.total_geral = (this.calcularCedulas() + this.calcularMoedas()).toLocaleString('pt-BR', { style: 'currency', currency: 'BRL'});

      this.salvarLocalStorage();
    },

    calcularCedulas() {
      return this.reais_2 * 2
        + this.reais_5 * 5
        + this.reais_10 * 10
        + this.reais_20 * 20
        + this.reais_50 * 50
        + this.reais_100 * 100;
    },

    calcularMoedas() {
      return this.reais_001 * 0.01
        + this.reais_005 * 0.05
        + this.reais_010 * 0.1
        + this.reais_025 * 0.25
        + this.reais_050 * 0.5
        + this.reais_1 * 1;
    },

    salvarLocalStorage() {
      let cedulas = this.getCedulas();
      let moedas = this.getMoedas();

      localStorage.setItem('cedulas', JSON.stringify(cedulas));
      localStorage.setItem('moedas', JSON.stringify(moedas));
    },

    getCedulas() {
        return {
          reais_2: parseInt(this.reais_2),
          reais_5: parseInt(this.reais_5),
          reais_10: parseInt(this.reais_10),
          reais_20: parseInt(this.reais_20),
          reais_50: parseInt(this.reais_50),
          reais_100: parseInt(this.reais_100),
          total_cedulas: this.total_cedulas
        }
    },

    getMoedas() {
      return {
        reais_001: parseInt(this.reais_001),
        reais_005: parseInt(this.reais_005),
        reais_010: parseInt(this.reais_010),
        reais_025: parseInt(this.reais_025),
        reais_050: parseInt(this.reais_050),
        reais_1: parseInt(this.reais_1),
        total_moedas: this.total_moedas
      }
    },

    buscarValoresLocalStorage(resetar) {
      let cedulas = JSON.parse(localStorage.getItem('cedulas'));
      let moedas = JSON.parse(localStorage.getItem('cedulas'));

      this.setarValoresCedulasMoedasTotais(cedulas, moedas, resetar);
    },

    setarValoresCedulasMoedasTotais(cedulas, moedas, resetar) {
      for (const property in cedulas) {
        if(cedulas[property] != null) {
          this[property] = resetar ? '' : cedulas[property];
        }
      }

      for (const property in moedas) {
        if(moedas[property] != null) {
          this[property] = resetar ? '' : moedas[property];
        }
      }
    },
    
    confirmarResetar() {
      this.dialog = true;
    },

    limparLocalStorage() {
      this.inicializar(true);
      this.dialog = false;
    }
  }
};
</script>
