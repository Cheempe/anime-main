<template>
    <header :class="$style.frameParent">
      <div :class="$style.nameWrapper">
        <h2 :class="$style.name">Name</h2>
      </div>
      <div :class="$style.navigationArea">
        <div :class="$style.searchButtonWrapper">
          <div :class="$style.searchButton">
            <div :class="$style.search">
              <!-- <img :class="$style.image18Icon" alt="" src="/image-18@2x.png" /> -->
              <input :class="$style.search1" placeholder="Search..." type="text" />
            </div>
          </div>
        </div>
        <div :class="$style.authOptions">
          <div :class="$style.loginregister">
            <div :class="$style.loginForm">
              <button @click="goLogin" :class="$style.loginButton">Login</button>
            </div>
            <button @click="goRegister" :class="$style.registerButton">Register</button>
          </div>
        </div>
      </div>
    </header>
  </template>
  
  <script setup lang="ts">
  import { useRouter } from "vue-router";
  import { onMounted } from "vue";
  
  const router = useRouter();
  
  const goLogin = () => {
    router.push("/login"); // Change the route path as needed
  };
  
  const goRegister = () => {
    router.push("/register"); // Change the route path as needed
  };
  </script>
  
  <style scoped module>
  .name {
    margin: 0;
    font-size: 1rem;
    font-weight: 600;
    white-space: nowrap;
  }
  
  .nameWrapper {
    padding-top: 0.5rem;
  }
  
  .search1 {
    width: 100%;
    border: none;
    outline: none;
    font-size: 1rem;
    background-color: transparent;
    height: 16px;
    color: black;
  }
  
  .search {
    border-radius: 9px;
    background-color: #e0e0e0;
    display: flex;
    align-items: center;
    padding: 0.25rem 0.75rem;
    gap: 0.5rem;
  }
  
  .searchButtonWrapper {
    padding: 0.75rem;
  }
  
  .login {
    font-size: 1rem;
    color: black;
  }
  
  .loginButton {
    cursor: pointer;
    border: none;
    padding: 0;
    background-color: transparent;
    color: inherit;
  }
  
  .loginForm {
    padding-top: 0.5rem;
  }
  
  .register {
    font-size: 1rem;
    color: white;
  }
  
  .registerButton {
    cursor: pointer;
    border: none;
    padding: 0.5rem 1rem;
    background-color: #800000;
    border-radius: 9px;
    color: inherit;
  }
  
  .registerButton:hover {
    background-color: #8b0000;
  }
  
  .loginregister {
    display: flex;
    gap: 1rem;
  }
  
  .authOptions {
    padding-top: 0.375rem;
  }
  
  .navigationArea {
    width: 449px; /* Adjust as needed */
    display: flex;
    align-items: center;
    gap: 1rem;
  }
  
  .frameParent {
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 1rem;
    font-size: 1.25rem;
    color: black;
  }
  
  @media screen and (max-width: 768px) {
    .navigationArea {
      width: auto;
      flex-grow: 1;
    }
  
    .frameParent {
      flex-wrap: wrap;
      gap: 0.5rem;
    }
  }
  </style>
  