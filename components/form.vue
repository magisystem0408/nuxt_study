<template>
  <v-stepper v-model="e1">
    <v-stepper-header>
      <v-stepper-step
        :complete="e1　>　1"
        step="1"
      >
        基本情報の入力
      </v-stepper-step>

      <v-divider></v-divider>

      <v-stepper-step
        :complete="e1>2"
        step="2"
      >
        予約日の確定
      </v-stepper-step>

      <v-stepper-step
        :complete="e1>3"
        step="3"
      >
        入力情報のご確認
      </v-stepper-step>
    </v-stepper-header>

    <v-stepper-items>
      <v-stepper-content step="1">
        <v-card
        class="mb-12"
        color="grey lighten-1"
        height="200px"
        >ねこ</v-card>

      </v-stepper-content>
    </v-stepper-items>


  </v-stepper>
</template>

<script>
export default {
  name: "form",
  data(){
    return{
      e1:1
    }
  }
}
</script>

<style scoped>

</style>
