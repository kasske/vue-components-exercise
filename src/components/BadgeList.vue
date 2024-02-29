<template>
  <section>
    <base-card>
    <!-- header slot -->

    <!-- didnt call header slot => it renders the default -->

      <!-- default slot unnamed (it can be only one unnamed) -->
      <template v-slot:default>          
        <ul>
          <li>
            <base-badge type="admin" caption="ADMIN"></base-badge>
          </li>
          <li>
            <base-badge type="author" caption="AUTHOR"></base-badge>
          </li>
        </ul>
      </template>

    </base-card>
  </section>
</template>

<script>
  export default {
    
  }
</script>

<!-- scoped => only for this file -->
<style scoped>
section h2 {
  margin: 0.5rem 0;
  color: #3a3a3a;
}

ul {
  list-style: none;
  margin: 0;
  padding: 0;
  display: flex;
  flex-direction: row;
}

li {
  margin-right: 1rem;
}
</style>