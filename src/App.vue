<template>
  <v-app style="margin: 10px; padding: 10px; width: 100%">
    <v-app-bar class="container" color="white"  
        flat style="margin: 0px; padding: 10px; width: 100%;
                              display:flex;
                              justify-content: space-around;">
      <v-card class="login" style="margin-left:10px;margin-right:50px;margin-top:0px;width:auto;
                              display:flex;
                              flex-wrap: wrap;
                              flex-flow: row wrap;
                              justify-content: flex-start;
                              width:160px;" flat tile >
                              <h3>Login Form</h3></v-card>
      
      <v-card class="card-btn" flat tile style="
                              display: flex;
                              flex-wrap: wrap;
                              flex-flow: row wrap;
                              justify-content: space-evenly;
                              margin-right:10px;
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

    <v-main >
        <v-form class="container" ref="form" v-model="valid" lazy-validation style="width:80%;">
            <v-row style="display:flex;">
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
                              justify-content: center;"
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
  methods:{
    validate () {
        if(this.$refs.form.validate())
          alert('Success!')
        
      },
  }
};
</script>
<style>
.btn{
  background-color:rgb(233, 231, 245);  
}

.btn:hover{
  color:rgb(231, 228, 245);
}
.container{
  display: flex;
  flex-direction: row;
}
div.container{
  background-color:rgb(235, 243, 235);
  border-radius: 3px;
  height: 100px;
}
fieldset{
  background-color: white;
}
</style>