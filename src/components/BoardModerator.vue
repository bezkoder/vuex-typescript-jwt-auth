<template>
  <div class="container">
    <header class="jumbotron">
      <h3>{{ content }}</h3>
    </header>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import UserService from "@/services/UserService";

@Component
export default class ModeratorBoard extends Vue {
   private content = "";

  mounted() {
    UserService.getModeratorBoard().then(
      (response) => {
        this.content = response.data;
      },
      (error) => {
        this.content =
          (error.response && error.response.data && error.response.data.message) ||
          error.message ||
          error.toString();
      }
    );
  }
}
</script>
