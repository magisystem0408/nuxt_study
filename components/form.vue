<template>
  <!--  <v-app>-->
  <!--    <v-app-bar color="primary" dark app>-->
  <!--      <v-toolbar-title>マルチステップアンケートの実装テスト</v-toolbar-title>-->
  <!--    </v-app-bar>-->

  <!--    <v-main>-->
  <!--      <v-container>-->
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
        <v-form>
          <v-container fluid>
            <v-row>
              <v-col
                cols="12"
                md="6"
              >
                <v-text-field
                  v-model="form.first"
                  :rules="nameRules"
                  :counter="10"
                  label="姓"
                  required
                ></v-text-field>
              </v-col>

              <v-col
                cols="12"
                md="6">
                <v-text-field
                  v-model="form.last"
                  :rules="nameRules"
                  :counter="10"
                  label="名"
                  required
                ></v-text-field>
              </v-col>

              <v-col
                cols="12"
                md="6"
              >
                <v-text-field
                  v-model="form.email"
                  :rules="emailRules"
                  label="メールアドレス"
                  required
                >

                </v-text-field>
              </v-col>

              <v-col
                cols="12"
                md="6"
              >
                <v-text-field
                  v-model="form.phoneNumber"
                  label="電話番号"
                >
                </v-text-field>
              </v-col>
            </v-row>
          </v-container>
        </v-form>

        <v-btn
          :disabled="!valid"
          color="primary"
          class="mr-4"
          @click="e1=2,validate"
        >
          次に進む
        </v-btn>
      </v-stepper-content>

      <!--ここから質問2-->
      <v-stepper-content step="2">
        <v-form>
          <v-container>
            <v-row>
              <v-col
                cols="12"
                md="6"
              >
                <v-menu
                  ref="menu"
                  v-model="menu"
                  :close-on-content-click="false"
                  :return-value.sync="date"
                  transition="scale-transition"
                  offset-y
                  min-width="auto"
                >
                  <template v-slot:activator="{on,attrs}">
                    <v-text-field
                      v-model="date"
                      label="第一希望日時"
                      prepend-icon="mdi-calendar"
                      readonly
                      v-on="on"
                    ></v-text-field>
                  </template>
                  <v-date-picker
                    v-model="date"
                    no-title
                    scrollable
                  >
                    <v-spacer></v-spacer>
                    <v-btn
                      text
                      color="primary"
                      @click="menu=false"
                    >キャンセル
                    </v-btn>
                    <v-btn
                      text
                      color="primary"
                      @click="$refs.menu.save(date)"
                    >OK
                    </v-btn>
                  </v-date-picker>


                </v-menu>

              </v-col>

              <v-col
                cols="12"
              >
                <v-textarea
                  v-model="form.bio"
                  color="teal"
                >
                  <template v-slot:label>
                    <div>
                      ご希望がございましたらお書きください<small>※任意</small>
                    </div>
                  </template>

                </v-textarea>

              </v-col>


            </v-row>
          </v-container>

        </v-form>


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
        <!--        <v-card-->
        <!--          class="mb-12"-->
        <!--          color="grey lighten-1"-->
        <!--          height="200px"-->
        <!--        >-->
        <h1>入力情報のご確認</h1>
        姓：{{ form.first }}
        名：{{ form.last }}
        メールアドレス：{{ form.email }}}
        電話番号：{{ form.phoneNumber }}
        <!--        </v-card>-->
        <br>
        <v-btn
          color="primary"
        >送信する
        </v-btn>
        <v-btn
          @click="e1=2"
        >戻る
        </v-btn>


      </v-stepper-content>


    </v-stepper-items>


  </v-stepper>

  <!--      </v-container>-->
  <!--    </v-main>-->
  <!--  </v-app>-->
</template>


<script>

export default {
  name: "Form",
  data() {

    // 入力値を格納
    const defaultForm = Object.freeze({
      first: '',
      last: '',
      email: '',
      phoneNumber: '',
      bio: '',

    })

    return {
      form: Object.assign({}, defaultForm),
      e1: 1,
      valid: true,

      date: new Date().toISOString().substr(0, 10),
      menu: false,
      modal: false,
      menu2: false,

      nameRules: [
        v => !!v || '入力してください',
        v => (v && v.length <= 10) || 'お前はネコマムシに近い存在だ！'
      ],

      emailRules: [
        v => !!v || '入力してください',
        v => /.+@.+\..+/.test(v) || '正しくメール打たないとマムシになるよ？'
      ]
    }
  },
  methods: {
    validate() {
      this.$refs.form.validate()
    }
  }
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
