<template>
  <v-navigation-drawer
    v-model="drawer1"
    app
    color="#000000"
    mini-variant
    mini-variant-width="110"
    right
  >
    <router-link to="/admin">
      <v-avatar class="d-block text-center mx-auto mt-4 mb-10" size="80">
      <v-btn class="ma-2" outlined large fab color="white"> 
        <v-img
          src="data:image/jpeg;base64,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"
          class="image"
        ></v-img>
      </v-btn>
    </v-avatar>
    </router-link>

    <!-- <v-card flat color="#6F0DFF" class="rounded-xl mx-4 py-10 text-center top">
      <v-btn icon dark class="mb-5">
        <v-icon>fas fa-sort-amount-up-alt</v-icon>
      </v-btn>
      <span class="white--text">Create<br />Order</span>
    </v-card> -->

    <div
      style="
        position: absolute;
        bottom: 20px;
        margin-left: auto;
        margin-right: auto;
        left: 0;
        right: 0;
        text-align: center;
      "
    >
      <v-btn dark class="changewith mb-3">
        <v-icon class="">mdi-bell</v-icon> </v-btn
      ><br />
      <v-badge bordered color="#6F0DFF" dot overlap>
        <v-btn dark class="changewith">
          <v-icon class="">mdi mdi-message-outline</v-icon>
        </v-btn>
      </v-badge>
    </div>
  </v-navigation-drawer>
</template>

<script>
export default {
  data: () => ({
    selectedItem: 0,
    drawer1: null,
  }),
};
</script>

<style>
.v-btn:not(.v-btn--round).v-size--default.changewith {
  height: 45px !important;
  min-width: 30px !important;
  padding: 0 12px;
}
.top {
  margin-top: 150px;
}
</style>
