<template>
  <v-app>

    <v-app-bar color="primary" dark app>
      <v-toolbar-title>マルチステップアンケートの実装テスト</v-toolbar-title>
    </v-app-bar>

    <v-main>
      <v-container>
        <v-stepper v-model="e1" alt-labels>
          <v-stepper-header>
            <v-stepper-step
              :complete="e1>1"
              step="1"
            >
              基本情報の入力
            </v-stepper-step>
        <v-divider></v-divider>

            <v-stepper-step
              :complete="e1>2"
              step="2"
            >
              ご希望の要件
            </v-stepper-step>

            <v-divider></v-divider>
            <v-stepper-step step="3"
            >
              内容のご確認
            </v-stepper-step>
          </v-stepper-header>

          <v-stepper-items>

<!--ここから質問1-->
            <v-stepper-content step="1">
              <v-card
                class="mb-12"
                color="grey lighten-1"
                height="200px"
              >
              ここに入力情報がくるよん
              </v-card>
              <v-btn
              color="primary"
              @click="e1=2"
              >
                次に進む
              </v-btn>
            </v-stepper-content>
<!--ここから質問2-->
            <v-stepper-content step="2">
              <v-card
                class="mb-12"
                color="grey lighten-1"
                height="200px"
              ></v-card>

              <v-btn
              color="primary"
              @click="e1=3"
              >
                次に進む
              </v-btn>

              <v-btn
              @click="e1=1">
                戻る
              </v-btn>
            </v-stepper-content>
<!--ここから質問3-->
          <v-stepper-content step="3">
            <v-card
              class="mb-12"
              color="grey lighten-1"
              height="200px"
            >
              ここに入力するよん
            </v-card>
            <v-btn
              color="primary"
              >送信する</v-btn>
            <v-btn
              @click="e1=2"
            >戻る</v-btn>


          </v-stepper-content>


          </v-stepper-items>



        </v-stepper>



      </v-container>
    </v-main>
  </v-app>
</template>


<script>
export default {
  data() {
    return {
      e1: 1,
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
