<template>
  <div class="container">
<div >
    <h3>CALCULADORA DE IMC</h3>
    <div class="">
      <label class="" >Peso:</label>
      <div class="input-field col s6">
        <input id="weight" v-model="weight" ref="weight" placeholder="Ex.: 23" class="" type="number">
      </div>
      <label class="" >Altura:</label>
      <div class="input-field col s6">
        <input id="height" v-model="height" ref="height" placeholder="Ex.: 1,60" class="" type="number">
      </div>
    </div>
    <div class="container-margin">
      <button type="button" id="clean" @click="clearIMC()" class="btn waves-effect waves-light btn-margin-left">Limpar</button>
      <button type="button" id="calcular" @click="calculaImc()" class="btn waves-effect waves-light btn-margin-left">Calcular</button>
    </div>
    <div class="container-margin">
      <label id="result" class="result"></label>
    </div>
  </div>
  <div>
  <table class="table">
    <tbody>
    <tr>
      <td>IMC</td>
      <td>Resultado</td>
    </tr>
    <tr id="R1" ref="R1">
      <td>Menos do que 18,5</td>
      <td>Abaixo do peso</td>
    </tr>
    <tr id="R2" ref="R2">
      <td>Entre 18,5 e 24,9</td>
      <td>Peso normal</td>
    </tr>
    <tr id="R3" ref="R3">
      <td>Entre 25 e 29,9 </td>
      <td>Sobrepeso</td>
    </tr>
    <tr id="R4" ref="R4">
      <td>Entre 30 e 34,9</td>
      <td>Obesidade grau 1</td>
    </tr>
    <tr id="R5" ref="R5">
      <td>Entre 35 e 39,9</td>
      <td>Obesidade grau 2</td>
    </tr>
    <tr id="R6" ref="R6">
      <td>Mais do que 40</td>
      <td>Obesidade grau 3</td>
    </tr>
    </tbody>
  </table>
  </div>
  </div>
</template>

<script>
export default {
  data: () => ({
    height: '',
    weight: '',
    calculo: ''
  }),
  methods: {
			calculaImc: function() {
        if(this.weight > 0 && this.height > 0) {
          this.calculo = (this.weight/ (this.height * this.height));
          this.showTable();
        } else {
          alert("Por favor, preencha a altura e o peso!");
        }
			},
      showTable: function() {
      this.clearTable()
      var imc = this.calculo
      if (imc <= 18.5) {
        this.$refs.R1.style.background = '#2ab6a9';
        this.$refs.R1.style.color = "#f2f2f2";
      }
      else if (imc >= 18.6 && imc < 25) {
        this.$refs.R2.style.background = '#2ab6a9';
        this.$refs.R2.style.color = "#f2f2f2";
      }
      else if (imc >= 25 && imc < 30) {
        this.$refs.R3.style.background = '#2ab6a9';
        this.$refs.R3.style.color = "#f2f2f2";
      }
      else if (imc >= 30 && imc < 35) {
        this.$refs.R4.style.background = '#2ab6a9';
        this.$refs.R4.style.color = "#f2f2f2";
      }
      else if (imc >= 35 && imc < 40) {
        this.$refs.R5.style.background = '#2ab6a9';
        this.$refs.R5.style.color = "#f2f2f2";
      }
      else if (imc >= 40) {
        this.$refs.R6.style.background = '#2ab6a9';
        this.$refs.R6.style.color = "#f2f2f2";
      }
    },
    clearTable: function() {
      this.$refs.R1.style.background = 'white';
      this.$refs.R1.style.color = "rgba(0,0,0,0.87)";
      this.$refs.R2.style.background = 'white';
      this.$refs.R2.style.color = "rgba(0,0,0,0.87)";
      this.$refs.R3.style.background = 'white';
      this.$refs.R3.style.color = "rgba(0,0,0,0.87)";
      this.$refs.R4.style.background = 'white';
      this.$refs.R4.style.color = "rgba(0,0,0,0.87)";
      this.$refs.R5.style.background = 'white';
      this.$refs.R5.style.color = "rgba(0,0,0,0.87)";
      this.$refs.R6.style.background = 'white';
      this.$refs.R6.style.color = "rgba(0,0,0,0.87)";
    },
    clearIMC: function() {
      this.$refs["weight"].value = '';
      this.$refs["height"].value = '';
      this.height = undefined;
      this.weight = undefined;
      this.clearTable();
    }
	}
}
</script>

<style>
.table.striped tr:nth-child(odd) {
  background-color: #f2f2f2;
}

.table tr:first-child {
  font-weight: bold;
  background-color: #f2f2f2;
}

.table tr:first-child {
  font-weight: bold;
  background-color: #f2f2f2;
}

.table tr td:first-child {
  padding-left: 15px;
}

.table {
  font-family: Tahoma,Segoe,Verdana,sans-serif;
}

.container-margin {
  margin-bottom: 20px;
  margin-top: 20px;
}

.result {
  font-size: 30px;
  color: #26a69a;
}

.btn-margin-left {
  margin-left: 5px;
}
</style>
