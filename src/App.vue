<template>
  <div>
    <the-header></the-header>
    <badge-list></badge-list>
    <user-info
      :full-name="activeUser.name"
      :info-text="activeUser.description"
      :role="activeUser.role"
    ></user-info>
    <course-goals>
      <!-- when we want data from component where slot is used to the parent (CourseGoals) -->
      <template #default="slotProps">
        <h2>
          {{ slotProps.item }}
        </h2>
        <p>
          {{ slotProps.anotherProp }}
        </p>
      </template>
    </course-goals>

    <button @click="setSelectedComponent('active-goals')">Acttive goals</button>
    <button @click="setSelectedComponent('manage-goals')">Manage goals</button>
    <!-- <active-goals v-if="selectedComponent === 'active-goals'"></active-goals>
    <manage-goals v-if="selectedComponent === 'manage-goals'"></manage-goals> -->

    <!-- dynamic component -->
    <!-- keep alive doesnt remove data (state) when component is hidden and shown -->
    <keep-alive>
      <component :is="selectedComponent"></component>
    </keep-alive>
  </div>
</template>

<script>
import TheHeader from './components/TheHeader.vue';
import BadgeList from './components/BadgeList.vue';
import UserInfo from './components/UserInfo.vue';
import CourseGoals from './components/CourseGoals.vue';
import ActiveGoals from './components/ActiveGoals.vue';
import ManageGoals from './components/ManageGoals.vue';

export default {
  components: {
    TheHeader,
    BadgeList,
    UserInfo,
    CourseGoals,
    ActiveGoals,
    ManageGoals
  },
  data() {
    return {
      selectedComponent: 'active-goals',
      activeUser: {
        name: 'Kastriot Limani',
        description: 'Site owner and admin',
        role: 'admin',
      },
    };
  },
  methods: {
    setSelectedComponent(cmp) {
      this.selectedComponent = cmp;
    }
  }
};
</script>

<!-- styles that effect whole project, without scope so its global -->
<style>
html {
  font-family: sans-serif;
}

body {
  margin: 0;
}
</style>