<template>
  <v-app style="margin: 10px; padding: 10px; width: 100%,height:20px">
    <v-app-bar class="container" color="white"  
        flat style="margin: 0px; padding: 10px; width: 100%;
        display:flex;
        justify-content: space-around;
        
        ">

      <v-card class="login" style="margin-left:10px;margin-right:50px;margin-top:0px;width:auto;
      display:flex;
      flex-wrap: wrap;
      flex-flow: row wrap;
      justify-content: flex-start;
      width:160px;
      " flat tile ><h3>Login Form</h3></v-card>
      
      <v-card class="card-btn" flat tile style="
      display: flex;
       flex-wrap: wrap;
       flex-flow: row wrap;
        justify-content: space-evenly;
        margin-right:10px;
        margin-top:auto;
        
        " >
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

    <v-main style="display:none">
        <v-container fluid>
          <v-form class="">
              <v-row>
                <v-card class="">Enter login</v-card>
                <v-text-field
                    v-model="login"
                    label="Login"
                    outlined
                    :rules="[rules.required, rules.login, rules.min]"
                  ></v-text-field>
                <v-card class="">Enter password</v-card>
                  <v-text-field
                    v-model="password"
                    :append-icon="show ? 'mdi-eye' : 'mdi-eye-off'"
                    :rules="[rules.required, rules.min]"
                    :type="show ? 'text' : 'password'"
                    name="input-10-2"
                    label="Password"
                    hint="At least 8 characters"
                    @click:append="show = !show"
                    outlined
                  ></v-text-field>
              </v-row>
            </v-form>
        </v-container>
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
</style>