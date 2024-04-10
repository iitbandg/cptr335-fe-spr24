<!-- <script setup>
defineProps({
  msg: {
    type: String,
    required: true
  }
})
</script> -->

<script>
export default {
  data() {
    return {
      user: {
        firstName: '',
        lastName: '',
        email: '',
        balance: ''
      }
    }
  },
  methods: {
    async loadData() {
      try {
        const requestOptions = {
          method: 'GET',
          headers: {
            'Content-Type': 'application/json'
          }
        }
        const response = await fetch(`/be/getUserData`, requestOptions)
        const userData = await response.json()
        this.firstName = userData.firstName
        this.lastName = userData.lastName
        this.email = userData.email
        this.balance = userData.balance
        console.log('<<<< Stuff =', firstName)
      } catch (error) {
        console.error('Error loading user data:', error)
      }
    }
  },
  created() {
    this.loadData()
  }
}
</script>

<template>
  <div>
    <div class="user-update-link">
      <router-link to="/update">
        <a class="txt2">
          Update User
          <i class="fa fa-long-arrow-right m-l-5" aria-hidden="true"></i>
        </a>
      </router-link>
    </div>
    <div class="change-password">
      <a class="txt2" href="#"> Change Password </a>
    </div>
    <div class="user-info">
      <h1>Welcome {{ firstName }} {{ lastName }}!</h1>
      <p>Email: {{ email }}</p>
      <p>Current Balance: ${{ balance }}</p>
    </div>
  </div>
</template>

<style>
/*//////////////////////////////////////////////////////////////////
[ FONT ]*/

@font-face {
  font-family: Poppins-Regular;
  src: url('../assets/Login/fonts/poppins/Poppins-Regular.ttf');
}

@font-face {
  font-family: Poppins-Bold;
  src: url('../assets/Login/fonts/poppins/Poppins-Bold.ttf');
}

@font-face {
  font-family: Poppins-Medium;
  src: url('../assets/Login/fonts/poppins/Poppins-Medium.ttf');
}

@font-face {
  font-family: Montserrat-Bold;
  src: url('../assets/Login/fonts/montserrat/Montserrat-Bold.ttf');
}

/*//////////////////////////////////////////////////////////////////
[ RESTYLE TAG ]*/

* {
  margin: 0px;
  padding: 0px;
  box-sizing: border-box;
}

body,
html {
  height: 100%;
  font-family: Poppins-Regular, sans-serif;
}

/*---------------------------------------------*/
a {
  font-family: Poppins-Regular;
  font-size: 14px;
  line-height: 1.7;
  color: #666666;
  margin: 0px;
  transition: all 0.4s;
  -webkit-transition: all 0.4s;
  -o-transition: all 0.4s;
  -moz-transition: all 0.4s;
}

a:focus {
  outline: none !important;
}

a:hover {
  text-decoration: none;
  color: #57b846;
}

/*---------------------------------------------*/
h1,
h2,
h3,
h4,
h5,
h6 {
  margin: 0px;
}

p {
  font-family: Poppins-Regular;
  font-size: 14px;
  line-height: 1.7;
  color: #666666;
  margin: 0px;
}

ul,
li {
  margin: 0px;
  list-style-type: none;
}

/*//////////////////////////////////////////////////////////////////
[ Utility ]*/

.txt2 {
  font-family: Poppins-Regular;
  font-size: 13px;
  line-height: 1.5;
  color: #666666;
}

.user-update-link {
  text-align: right;
}

.change-password {
  text-align: right;
}

@media (min-width: 992px) {
}
</style>