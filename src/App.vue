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
          <router-link class="link" to="/Note">Notas</router-link>
          <router-link class="link" to="/planner">Crear un plan</router-link>
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
  --bg-color-secondary-light:#222222;
  --bg-color-primary-light:#3b3b3b;
  --bg-color-black-light:#2b2a2a;
  --color-grey:#8d8d8d;
  --color-accept-green:#008b00;
  --color-accept-red:#a80000;
}

*
{
  box-sizing:border-box;
  padding:0;
  margin:0;
  text-decoration: none;
}
* {
  overscroll-behavior: contain;
  overscroll-behavior-block: contain;
  scroll-behavior: contain;
}
body,html{
  height: 100vh
}

body{
  background-color: var(--bg-color-primary);
}

.wrapper{
  position: fixed;
  display: flex;
  flex-direction: row;
  flex: 1;
  width: 100%;
  height: 100vh;
  font-family: 'Roboto Mono', monospace;
}

.container{
  position: relative;
  width:100%;
  &--flex{
    display: flex;
    flex: 1;
    gap: 5px;
  }
  &--col{
    flex-direction: column;
  }
  &--row{
    flex-direction: row;
  }
  &--pad-10{
      padding:10px;
  }
}
.input__wrapper{
  display: flex;
  flex-direction: column;
  gap: 10px;
  color: var(--color-grey);
  text-align: start;

  .input{
    width: 100%;
    outline: none;
    padding: 5px;
    font-family: 'Roboto Mono', monospace;
    border: var(--bg-color-primary-light) solid 2px;
    border-radius: 5px;
    background-color: var(--bg-color-secondary);
    font-size: 20px;
    color: var(--color-grey);
  }
  .textarea{
    resize: none;
    width: 100%;
    height: 100%;
    overflow: hidden;
  }

  .tags{
    display: flex;
    flex-direction: row;
    gap: 10px;
    width: 100%;
    max-width: 100%;
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

.button-group{
  display: flex;
  flex-direction: row;
  justify-content: end;
  gap: 10px;
  margin-top: 1em;
  .button{
    width: max-content;
    min-width: 100px;
    padding: 1em;
    outline: none;
    border: none;
    font-family: 'Roboto Mono', monospace;
    font-size: 17px;
    text-align: center;
    color: var(--color-grey);
    border: var(--bg-color-primary-light) solid 2px;
    border-radius: 5px;
    background-color: var(--bg-color-secondary);
    transition: all 0.3s;

    &--accept:hover{
      color: var(--color-accept-green);
      border: var(--color-accept-green) solid 2px;
      background-color: var(--bg-color-black-light);
    }
    &--decline:hover{
      color: var(--color-accept-red);
      border: var(--color-accept-red) solid 2px;
      background-color: var(--bg-color-black-light);
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
