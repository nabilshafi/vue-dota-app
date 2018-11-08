<template>
  <b-container fluid>
      <b-row>
        <b-col md="6" class="my-1">
          <b-pagination :total-rows="info.length" v-model="currentPage" hide-ellipsis class="my-0"/>
        </b-col>
        <b-col md="6" class="my-1">
          <b-form-group horizontal label="" class="mb-0">
            <b-input-group>
              <b-form-input v-model="filter" placeholder="Type to Search" />
              <b-input-group-append>
                <b-btn :disabled="!filter" @click="filter = ''">Clear</b-btn>
              </b-input-group-append>
            </b-input-group>
          </b-form-group>
        </b-col>
      </b-row>

      <b-table id="tableOne" striped hover bordered outlined:sort-by.sync="sortBy"
               :sort-desc.sync="sortDesc" :items="info" :fields="fields" :current-page="currentPage"
               :per-page="perPage" :filter="filter" @filtered="onFiltered"></b-table>
  </b-container>

</template>

<script>
  import axios from 'axios';
  import Bootstrapvue from 'bootstrap-vue';
  import moment from 'moment'
  export default {
    name: 'hello',
    data() {
      return {
        filter: null,
        currentPage: 1,
        perPage: 20,
        info: [],
        sortBy: "duration",
        sortDesc: true,
        fields: [
          {key: 'duration', sortable: true},
          {key: 'leagueid', sortable: true},
          {key: 'dire_name', sortable: true},
          {key: 'dire_score', sortable: true},
          {key: 'duration', sortable: true},
          {key: 'league_name', sortable: true},
          {key: 'leagueid', sortable: true},
          {key: 'match_id', sortable: true},
          {key: 'radiant_name', sortable: true},
          {key: 'radiant_score', sortable: true},
          {key: 'radiant_team_id', sortable: true},
          {key: 'radiant_win', sortable: true},
          {key: 'series_id', sortable: true},
          {key: 'series_type', sortable: true},
          {key: 'start_time', sortable: true}
        ],
      }
    },
    mounted() {
      /*formatter: (value) => {
        // return moment(value).format('MMMM Do YYYY, h:mm:ss a');
        return moment.unix(value);
      }*/
      var app = this;
      var http = axios.create({
        baseURL: "https://api.opendota.com/api/"
      });
      http.get('proMatches').then(response => {
        app.info = response.data;
        console.log("response, ", app.info);
      }).catch(e => {
        alert("Error: " + e.message);
      });
    },
    methods: {
      onFiltered (filteredItems) {
        // Trigger pagination to update the number of buttons/pages due to filtering
        this.totalRows = filteredItems.length
        this.currentPage = 1
      }
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>

  th {
    color: black !important;
    font-weight: bold !important;
    background-color: lightgray;
    height: 50px;
  }

</style>
