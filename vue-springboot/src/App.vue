<template>
    <div id="app" class="container-fluid">
        <div class="site-info">
            <h1 style="background: #0000FF; padding: 25px; color: #fff">Abudé Bittar</h1>
            <h3>Address Book using spring Boot</h3>
        </div>
        <nav>
            <router-link class="btn btn-primary" to="/">Customers</router-link>
            <router-link class="btn btn-primary" to="/add">Add</router-link>
            <router-link class="btn btn-primary" to="/search">Search</router-link>
        </nav>
        <br/>
        <router-view/>
    </div>
</template>

<script>
export default {
  name: "app"
};
</script>

<style>
.site-info {
  color: blue;
  margin-bottom: 20px;
}

.btn-primary {
  margin-right: 6px;
}

.container-fluid {
  color: red;
  text-align: center;
}
</style>
