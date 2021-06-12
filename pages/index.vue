<template>
  <!--  {{message}}-->
  <v-app>

    <v-app-bar color="primary" dark app>
      <v-toolbar-title>マルチステップアンケートの実装テスト</v-toolbar-title>
    </v-app-bar>

    <v-main>
      <v-container>

        {{message}}
        <Form></Form>

      </v-container>
    </v-main>
  </v-app>
</template>


<script>
import form from "@/components/form";

export default {
  data() {
    return {
      message: "フォームの練習",
    }
  },
}
</script>

<style>
/*.container {*/
/*  margin: 0 auto;*/
/*  min-height: 100vh;*/
/*  display: flex;*/
/*  justify-content: center;*/
/*  align-items: center;*/
/*  text-align: center;*/
/*}*/

</style>
