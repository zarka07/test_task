<template>
  <v-app style="margin: auto; padding: auto; width: 100%">
    <v-app-bar class="container" color="white"  
        flat style="margin: 0px; padding: 10px;
                              display:flex;
                              justify-content: center;
                              margin:auto;
                              align-items:baseline;
                              width:auto;
                              ">
      <v-card class="login" style="margin-left:10px;margin-right:50px;margin-top:5px;width:auto;
                              
                              flex-wrap: wrap;
                              flex-flow: row wrap;
                              justify-content: left;
                              width:160px;
                              " flat tile >
                              <h3>Login Form</h3></v-card>
      
      <v-card class="card-btn" flat tile style="
                              display: flex;
                              flex-wrap: wrap;
                              flex-flow: row wrap;
                              justify-content: right;
                              align:right;
                              
                              margin-top:auto;" >
        <v-btn class="btn"
          onmouseover="this.style.color='rgb(76, 38, 247)';" 
          onmouseout="this.style.color='black';"
          rounded text style="
                              display:block;font-size:10px;
                              margin-left:10px;margin-top:auto;margin-right:5px;
                              margin-bottom:5px;
                              text-transform:none;">About Me</v-btn>
        <v-btn class="btn"
          onmouseover="this.style.color='rgb(76, 38, 247)';" 
          onmouseout="this.style.color='black';"
          rounded text style="
                              display:block;font-size:10px;
                              margin-left:10px;margin-top:auto;
                              margin-right:5px;margin-bottom:5px;
                              text-transform:none;">Your Files</v-btn>
        <v-btn class="btn" 
          onmouseover="this.style.color='rgb(76, 38, 247)';" 
          onmouseout="this.style.color='black'"
          rounded text style="
                              display:block;font-size:10px;
                              margin-left:10px;margin-top:auto;
                              margin-right:5px;margin-bottom:5px;
                              text-transform:none;">Access Settings</v-btn>
      </v-card>
    </v-app-bar>

    <v-main>
        <v-form class="container" ref="form" v-model="valid" lazy-validation style="width:80%;">
            <v-row style="display:flex;min-width:275px">
              <div class="container" style="display:flex;justify-content: space-evenly;
                              height:auto;width:100%;
                              align-items:baseline;flex-wrap: wrap;">
                <v-col cols="6" sm="4" style="">
                  <v-text-field
                    style="flex-flow: row wrap;
                              justify-content: center;"
                    v-model="login" label="Login" outlined
                    :rules="[rules.required, rules.login, rules.min]"
                  ></v-text-field>
                </v-col>

                <v-col cols="6" sm="4" style="">
                  <v-text-field
                    style="flex-flow: row wrap;
                              justify-content: center;
                              "
                    v-model="password" label="Password"   
                    outlined
                      :append-icon="show ? 'mdi-eye' : 'mdi-eye-off'"
                      :rules="[rules.required, rules.min]"
                      :type="show ? 'text' : 'password'"
                      name="input-10-2"
                      hint="At least 8 characters"
                      @click:append="show = !show"
                  ></v-text-field>
                </v-col>
                <v-btn
                  style="flex-flow: row wrap;
                              justify-content: center;"
                  :disabled="!valid"
                  color="success"
                  class="mr-4"
                  @click="validate"
                >
                  Enter
                </v-btn>
              </div>
            </v-row>
        </v-form>
      </v-main>
  </v-app>
</template>

<script>

export default {
  name: 'App',
  components: {
  },
  data () {
    return {
        valid: true,
        show: false,
        login:'',
        password: '',
        rules: {
          required: value => !!value || 'Required.',
          min: v => v.length >= 8 || 'Min 8 characters',
          login: value => {
            const pattern = /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/
            return pattern.test(value) || 'Invalid e-mail.'
        },
      }
  }
  },
  mounted () {
      console.log(this.$vuetify.breakpoint)
    },
  methods:{
    validate () {
        if(this.$refs.form.validate())
          alert('Success!')
        
      },
  },
  /*computed: {
      width () {
        switch (this.$vuetify.breakpoint.name) {
          case 'sm': return 400
          case 'md': return 500
           
          case 'lg': return 160
          
        }
      },
    },*/
};
</script>
<style>
.btn{
  background-color:rgb(233, 231, 245);  
}

div.container{
  background-color:rgb(239, 245, 239);
  border-radius: 3px;
  
}
fieldset{
  background-color: white;
}
</style>