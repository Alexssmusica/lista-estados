<template>
  <div>
    <div
      id="slogan"
      class="text-center"
    >
      <h1>Lista de Estados <span class="fa fa-check"></span></h1>
    </div>
    <div class="main">
      <div class="container">
        <div class="row">
          <div class="col-md">
            <h5>Estado <span class="badge badge-info">{{estados.length}}</span></h5>
            <div class="card">
              <div class="card-body">
                <ul class="list-group">
                  <li class="list-group-item" v-for="estado in estados" v-bind:key="estado">
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
                  <li class="list-group-item" v-for="sigla in siglas" v-bind:key="sigla">
                    {{sigla}}
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
import "bootstrap/dist/css/bootstrap.css";
import "font-awesome/css/font-awesome.css";

export default {
	name: "App",
	data: function () {
		return {
			estados: ["Paraná", "Amazonas"],
			siglas: ["PR", "AM"]
		};
	}
};
</script>

<style>
#slogan {
  margin-top: 30px;
  margin-bottom: 30px;
}

#main {
  background-color: #f1f1f1;
  padding: 30px;
  padding-bottom: 30px;
}
</style>
