<script>
import { RouterLink, RouterView } from 'vue-router'

export default {
  data() {
    return {


    }
  },
  methods: {
    toPage() {
      this.$router.push('/page');
    }
  },
}
</script>

<template>
  <div class="home-view">
    <h2>Expense Tracker</h2>
    <div class="information">
      <p>Account : </p><input type="text" placeholder="placeholder">
      <p>Password :</p> <input type="password" placeholder="placeholder">
    </div>
    <div class="btn-class">
      <button id="sign-up" type="button" @click="toPage">
        <RouterLink to="/page">Sign Up</RouterLink>
      </button>
      <button id="log-in" type="button">Log In</button>
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

      a {
        color: #fff;
        text-decoration: none;

        &:active {
          scale: 0.95%;
        }
      }
    }



    #sign-up {
      background-color: rgb(156, 156, 162);

      &:active {
        scale: 0.95%;
      }
    }

    #log-in {
      background-color: rgb(99, 133, 219);

      &:active {
        scale: 0.95%;
      }
    }
  }
}
</style>
