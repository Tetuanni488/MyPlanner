<template>
  <div class="container container--flex container--col container--pad-10">
      <div class="input__wrapper">
          <span class="input__label">Name</span>
          <input type="text" class="input" autocomplete="none">
      </div>
      <div class="input__wrapper ">
          <span class="input__label">Tags</span>
          <div class="tags">
              <span class="tags__item">Tag</span>
              <span class="tags__item">Tag</span>
              <span class="tags__item">Tag</span>
              <span class="tags__item">Tag</span>
              <input type="text" class="input">
          </div>
      </div>
      <div class="planner">
          <span class="planner__label">Edit:</span> 
          <div class="planner__wrapper">
              <div class="planner__tools"></div>
              <div class="planner__cards">
                  <div class="planner__card">
                      hols
                  </div>
                  <div class="planner__card">
                      hols
                  </div>
                  <div class="planner__card">
                      hols
                  </div>
                  <div class="planner__card">
                      hols
                  </div>
                  <div class="planner__card">
                      hols
                  </div>
                  <div class="planner__card">
                      hols
                  </div>
                  <div class="planner__card">
                      hols
                  </div>
              </div>
          </div>
      </div>
  </div>
</template>

<style lang="scss">

:root{
  --bg-color-primary:#292929;
  --bg-color-secondary:#181818;
  --bg-color-primary-light:#3b3b3b;
  --color-grey:#8d8d8d;
}

.planner{
    display: flex;
    flex-direction: column;
    gap: 10px;
    width: 100%;
    height: 100%;
    text-align: start;
    color: var(--color-grey);

    &__wrapper{
        display: flex;
        flex-direction: column;
        gap: 10px;
        width: 100%;
        height: 100%;
        padding: 10px;
        border: var(--bg-color-primary-light) solid 2px;
        border-radius: 5px;
        background-color: var(--bg-color-secondary);
    }
    &__tools{
        border-bottom: var(--bg-color-primary-light) solid 2px;
    }
    &__cards{
        display: grid;
        grid-template-columns: repeat(7,1fr);
        column-gap: 10px;
        width: 100%;
        height: 100%;
    }
    &__card{
        display: flex;
        width: 100%;
        height: 100%;
        padding: 0.5em;
        border: var(--bg-color-primary-light) solid 2px;
        border-radius: 5px;
        background-color: var(--bg-color-secondary);
    }
}

</style>