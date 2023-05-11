<script>
import { RouterLink, RouterView } from 'vue-router'

export default {
  data() {
    return {
      status: {
        balance: null,
        income: null,
        expense: null
      },
      account: null,
      password: null,

    }
  },
  methods: {
    toPage() {
      this.$router.push('/page');
      this.setStorage();
    },
    setStorage() {
      localStorage.setItem("account", this.account)
      localStorage.setItem("password", this.password)

    },
    setStatus() {
      localStorage.setItem("balance", 2000)
      localStorage.setItem("income", 4000)
      localStorage.setItem("expense", 2000)
    }
  },
}
</script>

<template>
  <div class="home-view">
    <h2>Expense Tracker</h2>
    <div class="information">
      <p>Account : </p><input id="account" type="text" placeholder="placeholder" v-model="account">
      <p>Password :</p> <input id="password" type="password" placeholder="placeholder" v-model="password">
    </div>

    <!-- btn area -->
    <div class="btn-class">
      <button id="sign-up" type="button">Sign Up
      </button>
      <button id="log-in" type="button" @click="toPage">
        <RouterLink to="/page" @click="setStatus">Log In
        </RouterLink>
      </button>
    </div>
  </div>
</template>
<style lang="scss" scoped>
.home-view {
  width: 100vw;
  height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;

  h2 {
    font-size: 48px;
    font-weight: bold;
    color: rgb(102, 160, 223);
  }

  .information {
    margin-top: 30px;

    p {
      font-size: 16px;
      color: rgb(148, 160, 160);
    }

    input {
      width: 300px;
      font-size: 18px;
      margin-top: 0px;
    }

    input::placeholder {
      color: rgb(193, 185, 180);
    }

  }

  .btn-class {
    width: 250px;
    display: flex;
    margin-top: 80px;
    justify-content: space-between;

    button {
      color: #fff;
      width: 100px;
      border-radius: 20px;
      transition: 0.3s;


    }



    #sign-up {
      background-color: rgb(156, 156, 162);

      &:active {
        scale: 0.95%;
      }
    }

    #log-in {
      background-color: rgb(99, 133, 219);

      a {
        color: #fff;
        text-decoration: none;

        &:active {
          scale: 0.95%;
        }
      }
    }
  }
}
</style>
