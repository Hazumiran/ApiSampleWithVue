<!-- <template>
  <h1>Hai</h1>
  <EmployeeListvue />
</template>

<script>
import EmployeeListvue from "./components/EmployeeList.vue";
export default {
  name: "App",
  components: {
    EmployeeListvue,
  },
};
</script> -->

<template>
  <div class="body">
    <nav class="navbar navbar-expand-lg bg-light">
      <div class="container-fluid">
        <a class="navbar-brand" href="#">Navbar</a>
        <button
          class="navbar-toggler"
          type="button"
          data-bs-toggle="collapse"
          data-bs-target="#navbarSupportedContent"
          aria-controls="navbarSupportedContent"
          aria-expanded="false"
          aria-label="Toggle navigation"
        >
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarSupportedContent">
          <ul class="navbar-nav me-auto mb-2 mb-lg-0">
            <li class="nav-item">
              <a class="nav-link active" aria-current="page" href="#">Home</a>
            </li>
            <li class="nav-item">
              <a class="nav-link" href="#">Link</a>
            </li>
            <li class="nav-item dropdown">
              <a
                class="nav-link dropdown-toggle"
                href="#"
                role="button"
                data-bs-toggle="dropdown"
                aria-expanded="false"
              >
                Dropdown
              </a>
              <ul class="dropdown-menu">
                <li><a class="dropdown-item" href="#">Action</a></li>
                <li><a class="dropdown-item" href="#">Another action</a></li>
                <li><hr class="dropdown-divider" /></li>
                <li>
                  <a class="dropdown-item" href="#">Something else here</a>
                </li>
              </ul>
            </li>
            <li class="nav-item">
              <a class="nav-link disabled">Disabled</a>
            </li>
          </ul>
          <form class="d-flex" role="search">
            <input
              class="form-control me-2"
              type="search"
              placeholder="Search"
              aria-label="Search"
            />
            <button class="btn btn-outline-success" type="submit">
              Search
            </button>
          </form>
        </div>
      </div>
    </nav>
  </div>
  <div class="row">
    <div
      v-for="item in list"
      :key="item"
      class="col-sm-4 card"
      style="width: 18rem"
    >
      <img v-bind:src="`${item.urlToImage}`" />

      <div class="card-body">
        <h5 class="card-title">{{ item.title }}</h5>
        <p class="card-text">
          Some quick example text to build on the card title and make up the
          bulk of the card's content.
        </p>
        <a href="#" class="btn btn-primary">Go somewhere</a>
      </div>
    </div>
  </div>

  <!-- <ul>
    <li v-for="item in list" :key="item">
      {{ item.author }} {{ item.title }}
      <img v-bind:src="`${item.urlToImage}`" />
    </li>
  </ul> -->
</template>

<script>
import axios from "axios";
export default {
  name: "EmployeList",
  data() {
    return {
      list: [],
    };
  },
  async mounted() {
    let list = await axios.get(
      "https://newsapi.org/v2/everything?q=apple&from=2022-09-04&to=2022-09-04&sortBy=popularity&apiKey=fbc7df6d66804730afc384ca0bc388e3"
    );
    console.warn("data :", list.data.articles);
    this.list = list.data.articles;
  },
};
</script>

<style>
.card {
  top: 70px;
  align-content: center;
  margin: auto;
  text-align: center;
}
.row {
  width: 100%;
  align-content: center;
}
.body {
  position: fixed;
  z-index: 1;
  width: 100%;
  text-align: center;
}
</style>
