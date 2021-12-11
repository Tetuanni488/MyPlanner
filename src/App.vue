<template>
  <div class="wrapper">
    <nav class="navbar">
      <div class="navbar__logo">
        <img alt="Vue logo" src="./assets/logo.png">
      </div>
      <div class="dropdown">
        <div class="dropdown__button"> <div>This</div> <span class="material-icons">add</span></div>
        <div class="dropdown__content">
          <router-link class="link" to="/">Home</router-link>
          <router-link class="link" to="/about">About</router-link>
          <router-link class="link" to="/note">Home</router-link>
          <router-link class="link" to="/">Home</router-link>
        </div>
      </div>
    </nav>
    <router-view class="main-content" />
  </div>
</template>

<style lang="scss">

@import url('https://fonts.googleapis.com/css2?family=Lato:wght@400;900&family=Roboto+Mono&display=swap');

:root{
  --bg-color-primary:#292929;
  --bg-color-secondary:#181818;
  --bg-color-primary-light:#3b3b3b;
  --color-grey:#8d8d8d;
}

*{
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body{
  background-color: var(--bg-color-primary);
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
}

.wrapper{
  position: fixed;
  display: flex;
  flex-direction: row;
  width: 100%;
  min-height: 100%;
}

.container{
  position: relative;
  width:100%;
  min-height: 100%;
  padding:10px;

  &--flex{
    display: flex;
    gap: 5px;
  }
  &--col{
    flex-direction: column;
  }
}
.input__wrapper{
  display: flex;
  flex-direction: column;
  gap: 10px;
  color: var(--color-grey);
  text-align: start;

  &.input__label{
    font-size: 25px;
  }
  .input{
    width: 100%;
    outline: none;
    padding: 5px;
    border: var(--bg-color-primary-light) solid 2px;
    border-radius: 5px;
    background-color: var(--bg-color-secondary);
    font-size: 20px;
    color: var(--color-grey);
  }

  .tags{
    display: flex;
    flex-direction: row;
    gap: 10px;
    width: 100%;
    padding: 10px;
    border: var(--bg-color-primary-light) solid 2px;
    border-radius: 5px;
    background-color: var(--bg-color-secondary);
    


    &__item{
      text-align: center;
      padding: 5px;
      border: var(--bg-color-primary-light) solid 2px;
      border-radius: 5px;
      background-color: var(--bg-color-secondary);
    }

    .input{
      outline: none;
      border: none;
      padding: 5px;
      font-size: 20px;
      color: var(--color-grey);
    }
  }
}

.navbar{
  position: relative;
  display: flex;
  flex-direction: column;
  gap: 10px;
  width: auto;
  min-height: 100%;
  padding: 10px;
  font-family: 'Lato', sans-serif;
  font-weight: bold;
  background-color: var(--bg-color-secondary);
  color: #fff;

  &__logo{
    justify-self: center;

    img{
      width: 100px;
    }
  }
}


.dropdown{
  display: flex;
  flex-direction: column;
  flex:1;
  gap: 5px;
  width: 100%;
}
.dropdown__button{
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: space-between;
  gap: 5px;
  min-width:200px;

  span{
    font-size: 18px;
    font-weight: normal;
    color: var(--color-grey);
    transition: all 0.3s;
  }
  span:hover{
    cursor: pointer;
    color:#fff;
  }
}
.dropdown__content{
  display: flex;
  flex-direction: column;
  gap: 5px;
  margin-left: 1em;
  align-self: start;
  font-size: 15px;
  font-weight: normal;
}

.link{
  text-align: start;
  text-decoration: unset;
  color: var(--color-grey);
  font-family: 'Roboto Mono', monospace;
  transition: all 0.3s;
}
.link:hover{
  color: #fff;
}

.main-content{
  font-family: 'Roboto Mono', monospace;
  width: 100%;
}
</style>
