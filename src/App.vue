<template>
  <div>
    <div
      id="app"
      class="text-center"
    >
      <h1><span class="fa fa-list" /> Lista de Estados</h1>
    </div>
    <div class="main">
      <div class="container">
        <div class="row">
          <div class="col-md">
            <h5>Estados <span class="badge badge-info">{{estados.length}}</span></h5>
            <div class="card">
              <div class="card-body">
                <ul class="list-group">
                  <li
                    class="list-group-item"
                    v-for="estado in estados"
                    v-bind:key="estado"
                  >
                    {{estado}}
                  </li>
                </ul>
              </div>
            </div>
          </div>
          <div class="col-md">
            <h5>Siglas <span class="badge badge-info">{{siglas.length}}</span></h5>
            <div class="card">
              <div class="card-body">
                <ul class="list-group">
                  <li
                    class="list-group-item"
                    v-for="sigla in siglas"
                    v-bind:key="sigla"
                  >
                    {{sigla}}
                  </li>
                </ul>
              </div>
            </div>
          </div>
          <div class="col-md">
            <h5>Capitais <span class="badge badge-info">{{capitais.length}}</span></h5>
            <div class="card">
              <div class="card-body">
                <ul class="list-group">
                  <li
                    class="list-group-item"
                    v-for="capital in capitais"
                    v-bind:key="capital"
                  >
                    {{capital}}
                  </li>
                </ul>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios/dist/axios";
import "bootstrap/dist/css/bootstrap.css";
import "font-awesome/css/font-awesome.css";

export default {
	name: "App",
	data: function() {
		return {
			estados: [],
			siglas: [],
			capitais: []
		};
	},

	created() {
		axios({
			url: "http://localhost:4000/graphql",
			method: "post",
			data: {
				query: `
          {
            ufs {              
              nome
              uf
              capital
            }
         }
        `
			}
		}).then(response => {
			const query = response.data;
			this.estados = query.data.ufs.map(estado => estado.nome);
			this.siglas = query.data.ufs.map(sigla => sigla.uf);
			this.capitais = query.data.ufs.map(capital => capital.capital);
		});
	}
};
</script>

<style>
#app {
  margin-top: 30px;
  margin-bottom: 30px;
}

#main {
  background-color: #f1f1f1;
  padding: 30px;
  padding-bottom: 30px;
}
</style>
