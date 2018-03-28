<template>
  <div id="app">
    <!-- <p>{{syndrome}}</p> -->
    <h1>STEP {{step}}</h1>
    <p>Input R</p>
    <p>Click on a value to change the value</p>
    <p v-if="step === 0">
      <v-btn @click="changeR(0, r[0])">{{r[0]}}</v-btn>
      <v-btn @click="changeR(1, r[1])">{{r[1]}}</v-btn>
      <v-btn @click="changeR(2, r[2])">{{r[2]}}</v-btn>
      <v-btn @click="changeR(3, r[3])">{{r[3]}}</v-btn>
      <v-btn @click="changeR(4, r[4])">{{r[4]}}</v-btn>
      <v-btn @click="changeR(5, r[5])">{{r[5]}}</v-btn>
      <v-btn @click="changeR(6, r[6])">{{r[6]}}</v-btn>
      <v-btn @click="changeR(7, r[7])">{{r[7]}}</v-btn>
      <v-btn @click="changeR(8, r[8])">{{r[8]}}</v-btn>
      <v-btn @click="changeR(9, r[9])">{{r[9]}}</v-btn>
      <v-btn @click="changeR(10, r[10])">{{r[10]}}</v-btn>
      <v-btn @click="changeR(11, r[11])">{{r[11]}}</v-btn>
      <v-btn @click="changeR(12, r[12])">{{r[12]}}</v-btn>
      <v-btn @click="changeR(13, r[13])">{{r[13]}}</v-btn>
      <v-btn @click="changeR(14, r[14])">{{r[14]}}</v-btn>
      <v-btn @click="changeR(15, r[15])">{{r[15]}}</v-btn>
      <v-btn @click="changeR(16, r[16])">{{r[16]}}</v-btn>
      <v-btn @click="changeR(17, r[17])">{{r[17]}}</v-btn>
      <v-btn @click="changeR(18, r[18])">{{r[18]}}</v-btn>
      <v-btn @click="changeR(19, r[19])">{{r[19]}}</v-btn>
      <v-btn @click="changeR(20, r[20])">{{r[20]}}</v-btn>
      <v-btn @click="changeR(21, r[21])">{{r[21]}}</v-btn>
      <v-btn @click="changeR(22, r[22])">{{r[22]}}</v-btn>
      <v-btn @click="changeR(23, r[23])">{{r[23]}}</v-btn>
      <br/><v-btn @click="step ++">Go NExt</v-btn>
    </p>
    <table v-if="step === 1">
      <tr>
        <th>H^T</th>
        <th>       </th>
        <th>R</th>
        <th></th>
        <th>Syndrome</th>
      </tr>
      <tr>
        <th>
        {{returnHT[0]}}<br/>
        {{returnHT[1]}}<br/>
        {{returnHT[2]}}<br/>
        {{returnHT[3]}}<br/>
        {{returnHT[4]}}<br/>
        {{returnHT[5]}}<br/>
        {{returnHT[6]}}<br/>
        {{returnHT[7]}}<br/>
        {{returnHT[8]}}<br/>
        {{returnHT[9]}}<br/>
        {{returnHT[10]}}<br/>
        {{returnHT[11]}}<br/>
        {{returnHT[12]}}<br/>
        {{returnHT[13]}}<br/>
        {{returnHT[14]}}<br/>
        {{returnHT[15]}}<br/>
        {{returnHT[16]}}<br/>
        {{returnHT[17]}}<br/>
        {{returnHT[18]}}<br/>
        {{returnHT[19]}}<br/>
        {{returnHT[20]}}<br/>
        {{returnHT[21]}}<br/>
        {{returnHT[22]}}<br/>
        {{returnHT[23]}}<br/>
        </th>
        <th>   X   </th>
        <th>{{r}}</th>
        <th>===</th>
        <th v-if="syndrome === null"><v-btn @click="calculateSyndrome">Calculate</v-btn></th>
        <th v-else>{{syndrome}}</th>
        <th><v-btn v-if="step === 1 && syndrome !== null" @click="stepTwo">StepTwo</v-btn></th>
      </tr>
    </table>
    <table v-if="step === 2">
      <tr>
        <th v-if="weight !== null">Syndrom {{syndrome}} weight = {{weight}}</th>
      </tr>
      <tr v-if="weight <= 3">
        <th>
          <p>Syndrom.weight is <= 3 So</p>
          <p>e === {{ifWeightLessThanThree}}</p>
          <p>then v* === {{ifWeightLessThanThree}} + {{r}} === {{v}}</p>
        </th>
      </tr>
      <v-btn v-if="weight > 3" @click="step += 1">Step Three</v-btn>
    </table>
    <table v-if="step === 3">
      <tr>
        <th>{{returnP[0]}}</th>
        <th> + </th>
        <th>{{syndrome}}</th>
        <th> = </th>
        <th>{{e(returnP[0], syndrome)}}</th>
        <th> >> Weight == </th>
        <th>{{eWeight(returnP[0], syndrome, 0)}}</th>
      </tr>
      <tr>
        <th>{{returnP[1]}}</th>
        <th> + </th>
        <th>{{syndrome}}</th>
        <th> = </th>
        <th>{{e(returnP[1], syndrome)}}</th>
        <th> >> Weight == </th>
        <th>{{eWeight(returnP[1], syndrome, 1)}}</th>
      </tr>
      <tr>
        <th>{{returnP[2]}}</th>
        <th> + </th>
        <th>{{syndrome}}</th>
        <th> = </th>
        <th>{{e(returnP[2], syndrome)}}</th>
        <th> >> Weight == </th>
        <th>{{eWeight(returnP[2], syndrome, 2)}}</th>
      </tr>
      <tr>
        <th>{{returnP[3]}}</th>
        <th> + </th>
        <th>{{syndrome}}</th>
        <th> = </th>
        <th>{{e(returnP[3], syndrome)}}</th>
        <th> >> Weight == </th>
        <th>{{eWeight(returnP[3], syndrome, 3)}}</th>
      </tr>
      <tr>
        <th>{{returnP[4]}}</th>
        <th> + </th>
        <th>{{syndrome}}</th>
        <th> = </th>
        <th>{{e(returnP[4], syndrome)}}</th>
        <th> >> Weight == </th>
        <th>{{eWeight(returnP[4], syndrome, 4)}}</th>
      </tr>
      <tr>
        <th>{{returnP[5]}}</th>
        <th> + </th>
        <th>{{syndrome}}</th>
        <th> = </th>
        <th>{{e(returnP[5], syndrome)}}</th>
        <th> >> Weight == </th>
        <th>{{eWeight(returnP[5], syndrome, 5)}}</th>
      </tr>
      <tr>
        <th>{{returnP[6]}}</th>
        <th> + </th>
        <th>{{syndrome}}</th>
        <th> = </th>
        <th>{{e(returnP[6], syndrome)}}</th>
        <th> >> Weight == </th>
        <th>{{eWeight(returnP[6], syndrome, 6)}}</th>
      </tr>
      <tr>
        <th>{{returnP[7]}}</th>
        <th> + </th>
        <th>{{syndrome}}</th>
        <th> = </th>
        <th>{{e(returnP[7], syndrome)}}</th>
        <th> >> Weight == </th>
        <th>{{eWeight(returnP[7], syndrome, 7)}}</th>
      </tr>
      <tr>
        <th>{{returnP[8]}}</th>
        <th> + </th>
        <th>{{syndrome}}</th>
        <th> = </th>
        <th>{{e(returnP[8], syndrome)}}</th>
        <th> >> Weight == </th>
        <th>{{eWeight(returnP[8], syndrome, 8)}}</th>
      </tr>
      <tr>
        <th>{{returnP[9]}}</th>
        <th> + </th>
        <th>{{syndrome}}</th>
        <th> = </th>
        <th>{{e(returnP[9], syndrome)}}</th>
        <th> >> Weight == </th>
        <th>{{eWeight(returnP[9], syndrome, 9)}}</th>
      </tr>
      <tr>
        <th>{{returnP[10]}}</th>
        <th> + </th>
        <th>{{syndrome}}</th>
        <th> = </th>
        <th>{{e(returnP[10], syndrome)}}</th>
        <th> >> Weight == </th>
        <th>{{eWeight(returnP[10], syndrome, 10)}}</th>
      </tr>
      <tr>
        <th>{{returnP[11]}}</th>
        <th> + </th>
        <th>{{syndrome}}</th>
        <th> = </th>
        <th>{{e(returnP[11], syndrome)}}</th>
        <th> >> Weight == </th>
        <th>{{eWeight(returnP[11], syndrome, 11)}}</th>
      </tr>
      <tr v-if="minWeight < 3">
        <p>min weight {{minWeight}} >> w(S + Pi) = {{minWeightE}}</p>
        <p>THEN U === {{getU(minWeightIndex)}}</p>
        <p>THEN E === {{getFinalE(minWeightE, getU(minWeightIndex))}}</p>
        <p>THEN V === {{addVectore(r, getFinalE(minWeightE, getU(minWeightIndex)))}}</p>
      </tr>
      <tr>
        <div v-if="minWeight > 2">
        <br/>
        <br/>
        <br/>
        <tr>

        </tr>
        <tr>

        </tr>
        <th> {{syndrome}}  X   </th>
        <th>
        {{returnP[0]}}<br/>
        {{returnP[1]}}<br/>
        {{returnP[2]}}<br/>
        {{returnP[3]}}<br/>
        {{returnP[4]}}<br/>
        {{returnP[5]}}<br/>
        {{returnP[6]}}<br/>
        {{returnP[7]}}<br/>
        {{returnP[8]}}<br/>
        {{returnP[9]}}<br/>
        {{returnP[10]}}<br/>
        {{returnP[11]}}<br/>
        </th>
        <th>=== {{multiplyMatrix(syndrome, returnP)}} >> Weight = {{lastStepWeight}}</th>
        <div v-if="lastStepWeight === 2 || lastStepWeight === 3">
          E === {{getFinalE([0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0], lastStepWeight)}}
          V* === {{addVectore(r, getFinalE([0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0], lastStepWeight))}}
        </div>
        <div v-else>
          <tr>
            <th>{{returnP[0]}}</th>
            <th> + </th>
            <th>{{lastStteWeight(syndrome, returnP)}}</th>
            <th> = </th>
            <th>{{e(returnP[0], lastStteWeight(syndrome, returnP))}}</th>
            <th> >> Weight == </th>
            <th>{{eWeight(returnP[0], lastStteWeight(syndrome, returnP), 0)}}</th>
          </tr>
          <tr>
            <th>{{returnP[1]}}</th>
            <th> + </th>
            <th>{{lastStteWeight(syndrome, returnP)}}</th>
            <th> = </th>
            <th>{{e(returnP[1], lastStteWeight(syndrome, returnP))}}</th>
            <th> >> Weight == </th>
            <th>{{eWeight(returnP[1], lastStteWeight(syndrome, returnP), 1)}}</th>
          </tr>
          <tr>
            <th>{{returnP[2]}}</th>
            <th> + </th>
            <th>{{lastStteWeight(syndrome, returnP)}}</th>
            <th> = </th>
            <th>{{e(returnP[2], lastStteWeight(syndrome, returnP))}}</th>
            <th> >> Weight == </th>
            <th>{{eWeight(returnP[2], lastStteWeight(syndrome, returnP), 2)}}</th>
          </tr>
          <tr>
            <th>{{returnP[3]}}</th>
            <th> + </th>
            <th>{{lastStteWeight(syndrome, returnP)}}</th>
            <th> = </th>
            <th>{{e(returnP[3], lastStteWeight(syndrome, returnP))}}</th>
            <th> >> Weight == </th>
            <th>{{eWeight(returnP[3], lastStteWeight(syndrome, returnP), 3)}}</th>
          </tr>
          <tr>
            <th>{{returnP[4]}}</th>
            <th> + </th>
            <th>{{lastStteWeight(syndrome, returnP)}}</th>
            <th> = </th>
            <th>{{e(returnP[4], lastStteWeight(syndrome, returnP))}}</th>
            <th> >> Weight == </th>
            <th>{{eWeight(returnP[4], lastStteWeight(syndrome, returnP), 4)}}</th>
          </tr>
          <tr>
            <th>{{returnP[5]}}</th>
            <th> + </th>
            <th>{{lastStteWeight(syndrome, returnP)}}</th>
            <th> = </th>
            <th>{{e(returnP[5], lastStteWeight(syndrome, returnP))}}</th>
            <th> >> Weight == </th>
            <th>{{eWeight(returnP[5], lastStteWeight(syndrome, returnP), 5)}}</th>
          </tr>
          <tr>
            <th>{{returnP[6]}}</th>
            <th> + </th>
            <th>{{lastStteWeight(syndrome, returnP)}}</th>
            <th> = </th>
            <th>{{e(returnP[6], lastStteWeight(syndrome, returnP))}}</th>
            <th> >> Weight == </th>
            <th>{{eWeight(returnP[6], lastStteWeight(syndrome, returnP), 6)}}</th>
          </tr>
          <tr>
            <th>{{returnP[7]}}</th>
            <th> + </th>
            <th>{{lastStteWeight(syndrome, returnP)}}</th>
            <th> = </th>
            <th>{{e(returnP[7], lastStteWeight(syndrome, returnP))}}</th>
            <th> >> Weight == </th>
            <th>{{eWeight(returnP[7], lastStteWeight(syndrome, returnP), 7)}}</th>
          </tr>
          <tr>
            <th>{{returnP[8]}}</th>
            <th> + </th>
            <th>{{lastStteWeight(syndrome, returnP)}}</th>
            <th> = </th>
            <th>{{e(returnP[8], lastStteWeight(syndrome, returnP))}}</th>
            <th> >> Weight == </th>
            <th>{{eWeight(returnP[8], lastStteWeight(syndrome, returnP), 8)}}</th>
          </tr>
          <tr>
            <th>{{returnP[9]}}</th>
            <th> + </th>
            <th>{{lastStteWeight(syndrome, returnP)}}</th>
            <th> = </th>
            <th>{{e(returnP[9], lastStteWeight(syndrome, returnP))}}</th>
            <th> >> Weight == </th>
            <th>{{eWeight(returnP[9], lastStteWeight(syndrome, returnP), 9)}}</th>
          </tr>
          <tr>
            <th>{{returnP[10]}}</th>
            <th> + </th>
            <th>{{lastStteWeight(syndrome, returnP)}}</th>
            <th> = </th>
            <th>{{e(returnP[10], lastStteWeight(syndrome, returnP))}}</th>
            <th> >> Weight == </th>
            <th>{{eWeight(returnP[10], lastStteWeight(syndrome, returnP), 10)}}</th>
          </tr>
          <tr>
            <th>{{returnP[11]}}</th>
            <th> + </th>
            <th>{{lastStteWeight(syndrome, returnP)}}</th>
            <th> = </th>
            <th>{{e(returnP[11], lastStteWeight(syndrome, returnP))}}</th>
            <th> >> Weight == </th>
            <th>{{eWeight(returnP[11], lastStteWeight(syndrome, returnP), 11)}}</th>
          </tr>
        </div>
        <p v-if="minLAst === 2">
          E === {{getFinalE(getU(minLAstIndex), lastStteWeight(syndrome, returnP))}}
          v* === {{addVectore(r, getFinalE(getU(minLAstIndex), lastStteWeight(syndrome, returnP)))}}
        </p>
        <p v-else>
          Fail
        </p>
      </div>
      </tr>
      <!-- <th>{{math.add(returnP[0], syndrome)}}</th> -->
    </table>
  </div>
</template>

<script>
var math = require('mathjs')
export default {
  name: 'App',
  data: () => ({
    step: 0,
    minLAst: null,
    minLAstIndex: null,
    dialog: true,
    minWeight: null,
    minWeightE: null,
    syndrome: null,
    weight: 0,
    minWeightIndex: null,
    lastStepWeight: null,
    v: null,
    r: [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
    p: math.matrix([[1, 0, 0, 0, 1, 1, 1, 0, 1, 1, 0, 1],
      [0, 0, 0, 1, 1, 1, 0, 1, 1, 0, 1, 1],
      [0, 0, 1, 1, 1, 0, 1, 1, 0, 1, 0, 1],
      [0, 1, 1, 1, 0, 1, 1, 0, 1, 0, 0, 1],
      [1, 1, 1, 0, 1, 1, 0, 1, 0, 0, 0, 1],
      [1, 1, 0, 1, 1, 0, 1, 0, 0, 0, 1, 1],
      [1, 0, 1, 1, 0, 1, 0, 0, 0, 1, 1, 1],
      [0, 1, 1, 0, 1, 0, 0, 0, 1, 1, 1, 1],
      [1, 1, 0, 1, 0, 0, 0, 1, 1, 1, 0, 1],
      [1, 0, 1, 0, 0, 0, 1, 1, 1, 0, 1, 1],
      [0, 1, 0, 0, 0, 1, 1, 1, 0, 1, 1, 1],
      [1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0]]),
    ht: math.matrix([[1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
      [0, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
      [0, 0, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0],
      [0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0, 0],
      [0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0],
      [0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0],
      [0, 0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0],
      [0, 0, 0, 0, 0, 0, 0, 1, 0, 0, 0, 0],
      [0, 0, 0, 0, 0, 0, 0, 0, 1, 0, 0, 0],
      [0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 0, 0],
      [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 0],
      [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1],
      [1, 0, 0, 0, 1, 1, 1, 0, 1, 1, 0, 1],
      [0, 0, 0, 1, 1, 1, 0, 1, 1, 0, 1, 1],
      [0, 0, 1, 1, 1, 0, 1, 1, 0, 1, 0, 1],
      [0, 1, 1, 1, 0, 1, 1, 0, 1, 0, 0, 1],
      [1, 1, 1, 0, 1, 1, 0, 1, 0, 0, 0, 1],
      [1, 1, 0, 1, 1, 0, 1, 0, 0, 0, 1, 1],
      [1, 0, 1, 1, 0, 1, 0, 0, 0, 1, 1, 1],
      [0, 1, 1, 0, 1, 0, 0, 0, 1, 1, 1, 1],
      [1, 1, 0, 1, 0, 0, 0, 1, 1, 1, 0, 1],
      [1, 0, 1, 0, 0, 0, 1, 1, 1, 0, 1, 1],
      [0, 1, 0, 0, 0, 1, 1, 1, 0, 1, 1, 1],
      [1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0]
    ])
  }),
  beforeMount: function () {
    // this.calculateSyndrome()
  },
  computed: {
    returnP () {
      var mat = Object.values(this.p)[0]
      return mat
    },
    returnHT () {
      var mat = Object.values(this.ht)[0]
      return mat
    },
    ifWeightLessThanThree () {
      var e = []
      var v = []
      for (var j = 0; j < this.syndrome.length; j++) {
        e.push(this.syndrome[j])
      }
      for (var i = 0; i < 12; i++) {
        e.push(0)
      }
      v =  math.add(e, this.r)
      this.v = v
      for (var z = 0; z < v.length; z++) {
        if (v[z] > 1) {
          var res = e[z] % 2
          v.splice(z, 1, res)
        }
      }
      return e
    }
  },
  methods: {
    changeR (index, val) {
      if (val === 0) {
        this.r.splice(index, 1, 1)
      } else {
        this.r.splice(index, 1, 0)
      }
    },
    getFinalE (one, two) {
      var e = []
      for (var i = 0; i < one.length; i++) {
        e.push(one[i])
      }
      for (var j = 0; j < two.length; j++) {
        e.push(two[j])
      }
      return e
    },
    getU (index) {
      var u = [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0]
      u.splice(index, 1, 1)
      return u
    },
    addVectore (one, two) {
      var e = math.add(one, two)
      for (var i = 0; i < this.r.length; i++) {
        if (e[i] > 1) {
          var res = e[i] % 2
          e.splice(i, 1, res)
        }
      }
      return e
    },
    e (one, two) {
      var e = math.add(one, two)
      for (var i = 0; i < e.length; i++) {
        if (e[i] > 1) {
          var res = e[i] % 2
          e.splice(i, 1, res)
        }
      }
      return e
    },
    lastStteWeight (one, two, index) {
      var e = math.add(one, two)
      var weight = 0
      for (var i = 0; i < e.length; i++) {
        if (e[i] > 1) {
          var res = e[i] % 2
          e.splice(i, 1, res)
        }
      }
      for (var j = 0; j < e.length; j++) {
        if (e[j] === 1) {
          weight += 1
        }
      }
      if (this.minWeight === null) {
        this.minLAst = weight
        this.minWeightE = e
        this.minLAstIndex = index
      } else if (this.minWeight > weight) {
        this.minLAst = weight
        this.minWeightE = e
        this.minLAstIndex = index
      }
      return weight
    },
    eWeight (one, two, index) {
      var e = math.add(one, two)
      var weight = 0
      for (var i = 0; i < e.length; i++) {
        if (e[i] > 1) {
          var res = e[i] % 2
          e.splice(i, 1, res)
        }
      }
      for (var j = 0; j < e.length; j++) {
        if (e[j] === 1) {
          weight += 1
        }
      }
      if (this.minWeight === null) {
        this.minWeight = weight
        this.minWeightIndex = index
        this.minWeightE = e
      } else if (this.minWeight > weight) {
        this.minWeight = weight
        this.minWeightIndex = index
        this.minWeightE = e
      }
      return weight
    },
    stepTwo () {
      this.calculateWeight()
      this.step = 2
    },
    multiplyMatrix (one) {
      var result = math.multiply(one, this.p)
      var matrix = Object.values(result)[0]
      for (var i = 0; i < matrix.length; i++) {
        if (matrix[i] > 1) {
          var res = matrix[i] % 2
          matrix.splice(i, 1, res)
        }
      }
      var weight = 0
      for (var j = 0; j < matrix.length; j++) {
        if (matrix[j] === 1) {
          weight += 1
        }
      }
      this.lastStepWeight = weight
      return matrix
    },
    calculateSyndrome () {
      var result = math.multiply(this.r, this.ht)
      var matrix = Object.values(result)[0]
      for (var i = 0; i < matrix.length; i++) {
        if (matrix[i] > 1) {
          var res = matrix[i] % 2
          matrix.splice(i, 1, res)
        }
      }
      this.syndrome = matrix
    },
    calculateWeight () {
      var weight = 0
      for (var i = 0; i < this.syndrome.length; i++) {
        if (this.syndrome[i] === 1) {
          weight += 1
        }
      }
      this.weight = weight
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
