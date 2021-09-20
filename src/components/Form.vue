<template>
  <div class="counter">
<<<<<<< Updated upstream
    <h1>CARONTE</h1>
    <h2>Catcher of Ontological Terms</h2>
        <hr>

        <div class="card" style="width: 30rem;">
          <div class="card-body">
            <h5 class="card-title">Choose terms from Bioportal</h5>
            <p class="card-text"> Choose your option and submit it</p>
=======
    <h1> Welcome to Caronte</h1>
    <h4>Catcher of ontological terms</h4>
        <hr>
        <div class="card" style="width: 30rem;">
          <div class="card-body">
              <h5 class="card-title">Choose term from Bioportal</h5>
              <p class="card-text"> Choose your option and submit it</p>
>>>>>>> Stashed changes

              <div class="form-group">
                <label for="search">Term</label>
                <input type="text"
                      v-model="term">
              </div>
<<<<<<< Updated upstream
              <br>
              <div class="form-group">
                <label for="ontology">Ontology</label>
                <input type="text" placeholder="NCIT"
                      v-model="ontology">
              </div> 
              <br>
                <div id="example">
                  <button v-on:click="getBioportal(term)">Search</button>
                </div>

              <br>
=======
            <br>

            <div class="form-group">
              <label for="ontology">Ontology</label>
              <input type="text" placeholder="NCIT"
                    v-model="ontology">
            </div> 
            <br>

            <div id="example">
              <button v-on:click="getBioportal(term,ontology)">Search</button>
            </div>
>>>>>>> Stashed changes
            <select class="form-select" aria-label="Default select example">
              <option selected>Chosen Results:</option>

              <option v-for="l in list[0]"  v-bind:key="l" >
                <label for="selecty">{{ l }}</label>
              </option>

            </select>
<<<<<<< Updated upstream
            <br>
            <button type="button" class="btn btn-primary" v-on:click="getURL(selecty)">Submit</button>
            <br>
            <br>
            <p>{{result[0]}}</p>
=======
            <button type="button" class="btn btn-primary" v-on:click="getURL()">Submit</button>
>>>>>>> Stashed changes
          </div>
        </div>
        

      
  </div>
  

</template>

<script>
export default {

  name: 'Form',
  data() {
    return {
          term: '',
          ontology:'',
          list:[],
          respond:[],
          result: [],
    }
  },
  methods:{
    getBioportal: async function(term){
      var preurl='http://data.bioontology.org/'
      var id='http%3a%2f%2fncicb.nci.nih.gov%2fxml%2fowl%2fEVS%2fThesaurus.owl%23C3224';
      var apikey='53e05b90-e7f3-42ed-bac2-6b2857d52bb5';
      var fullurl = preurl + 'search?q=' + term + '&ontology=NCIT' +"&subtree_root_id="+id+"&apikey="+apikey;

      const response = await fetch(fullurl);
      var json = await response.json();
      console.log(json);
      this.respond.push(json);
      console.log(this.respond)


      var jp = require('jsonpath');
      var names = jp.query(json, 'collection[*].prefLabel');

      this.list=[];
      this.list.push(names);
      
      //console.log(names); 
    },
<<<<<<< Updated upstream
    getURL: function(selecty) {
      console.log(selecty)

      var messag = "Ocular Melanoma"
      var jp = require('jsonpath');
      var urly = jp.query(this.respond[0], 'collection[*].prefLabel'); // 'collection.0[?(@.@id=="${name}")]

      for (var i = 0; i < urly.length; i++) {
        if (urly[i] == messag){
          var result_url = this.respond[0]['collection'][`${i}`]['@id'];
          console.log(result_url);
          this.result.push(result_url)
        }
      }
=======
    getURL:function(){
      //console.log(this.respond[0]['collection'][0]['@id']);
      var jp = require('jsonpath');
      var names = jp.query('respond[0]', 'collection[*].@id[?(@.preflabel==Ocular Melanoma)]');
      console.log(names);

>>>>>>> Stashed changes

    }
    //$..book[?(@.price==8.95)]
  }
}

</script>


