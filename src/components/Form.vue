<template>
  <div class="counter">
    <h1> Welcome{{  }}</h1>

    <div class="form-group">
      <label for="search">Term</label>
      <input type="text"
            v-model="term">
    </div>

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

        <hr>


        <div class="card" style="width: 30rem;">
          <div class="card-body">
            <h5 class="card-title">Choose term from Bioportal</h5>
            <p class="card-text"> Choose your option and submit it</p>
            <select class="form-select" aria-label="Default select example">
              <option selected>Chosen Results:</option>
              <option value={{l}} v-for="l in list[0]"  v-bind:key="l" ><p>{{ l }}</p></option>
            </select>
            <button type="button" class="btn btn-primary">Primary</button>
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
    }
  },
  methods:{
    getBioportal: async function(term,ontology){
      var preurl='http://data.bioontology.org/'
      var id='http%3a%2f%2fncicb.nci.nih.gov%2fxml%2fowl%2fEVS%2fThesaurus.owl%23C3224';
      var apikey='53e05b90-e7f3-42ed-bac2-6b2857d52bb5';
      var fullurl = preurl + 'search?q=' + term + '&ontology='+ ontology +"&subtree_root_id="+id+"&apikey="+apikey;

      const response = await fetch(fullurl);
      var json = await response.json();
      //console.log(json);
      this.respond.push(json);
      console.log(this.respond)


      var jp = require('jsonpath');
      var names = jp.query(json, 'collection[*].prefLabel');

      /*
      var nam;
      for (nam in names){
        this.list.push(nam)
        console.log(nam);
      }
      */
      this.list=[];
      this.list.push(names);
      
      //console.log(names); 
    }
  }
}

</script>


