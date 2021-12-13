<template>
  <div class="container container--flex container--row container--pad-10">
    <div class="container container--flex container--col">
        <div class="input__wrapper">
            <span class="input__label">Notas</span>
        </div>
        <div class="notes-list">
            <div class="note-container" @click="viewNote(note.id)" v-bind:key="index" v-for="(note,index) in notes">
                <div class="note">
                    <span class="note__title">
                        {{note.title}}
                    </span>
                    <span class="note__title">
                        Creado el 8 de diciembre de 2021 a las 21:30 horas
                    </span>
                </div>
            </div>
        </div>
    </div>
    
    <div class="container container--flex container--col">
        <div class="input__wrapper">
            <span class="input__label">Title</span>
            <input type="text" class="input" autocomplete="none" v-model="selectedNote.title" placeholder="Put title here">
        </div>
        <div class="input__wrapper ">
            <span class="input__label">Tags</span>
            <div class="tags">
                <div class="tags__item" v-bind:key="index" v-for="(tag,index) in selectedNote.tags">
                    <span class="tags__item-name">{{tag}}</span>
                </div>
                <input type="text" class="input" @keyup.enter="addTag">
            </div>
        </div>
        <div class="input__wrapper ">
            <span class="input__label">Details</span>
            <textarea cols="30" rows="10" class="input textarea" v-model="selectedNote.detils" placeholder="What means this note for you?"></textarea>
        </div>
        <div class="button-group">
            <button v-if="notes[notes.findIndex(note =>{return note.id === selectedNote.id ;})]" class="button button--accept" @click="saveNote">GUARDAR</button>
            <button class="button button--accept" @click="createNote">CREAR</button>
            <button class="button button--decline">BORRAR</button>
        </div>
    </div>
  </div>
  <div class="modal__container">
      <div class="modal">
          <header class="modal__header">
              <h3 class="modal__title">¿Estas seguro?</h3>
          </header>
          <div class="modal__text">
              Una vez acepte realizar los cambios, ya no podra revertirlos.
          </div>
          <div class="modal__options">
              <button class="modal__button modal__button--accept" @click="updateNote" >ACEPTAR</button>
            <button class="modal__button modal__button--decline" @click="closeModal">CANCELAR</button>
          </div>
      </div>
  </div>
</template>

<script>
const $ = require("jquery");

export default {
  name: 'Notes',
  methods: {
    viewNote(id){
        let note = this.notes[this.notes.findIndex(note =>{
            return note.id === id ;
        })];
        if (note){
            this.selectedNote = note;
            console.log(note)
        }
    },
    addTag(event){
        this.selectedNote.tags.push(event.target.value)
    },
    saveNote(){
        let note = this.notes[this.notes.findIndex(note =>{
            return note.id === this.selectedNote.id ;
        })];
        if (note){
            $(".modal__container")
                .css("display", "flex")
                .hide()
                .fadeIn();
        }else{
            createNote()
        }
    },
    createNote(){
        this.selectedNote.id = this.notes.length
        console.log(this.notes)
        this.notes.push(this.selectedNote)
    },
    updateNote(){
        let note = this.notes[this.notes.findIndex(note =>{
            return note.id === this.selectedNote.id ;
        })];
        note = this.selectedNote;
        $(".modal__container").fadeOut()
    },
    closeModal(){
        $(".modal__container").fadeOut()
    }
  },
  data(){
    return{
        selectedNote: {
            id:"none",
            title:"",
            detils:"",
            tags:["Tanger","BniAhmed"]
        },
        notes:[
            {
            id:0,
            title: "Nota 1",
            detils:"What means this note for you?",
            tags:["Tanger","BniAhmed", "lol"]
            },
            {
            id:1,
            title: "Nota 2",
            detils:"What means this note for you?",
            tags:["Tanger","BniAhmed", "lol"]
            }
        ]
    }
  },
//   created(){
//     this.copyTodos = [...this.todos];
//   }
}
</script>

<style lang="scss">

:root{
  --bg-color-primary:#292929;
  --bg-color-secondary:#181818;
  --bg-color-secondary-light:#222222;
  --bg-color-primary-light:#3b3b3b;
  --bg-color-black-light:#2b2a2a;
  --bg-color-black-light--05:#2b2a2a73;
  --color-grey:#8d8d8d;
}

.notes-list{
    display: flex;
    flex-direction: column;
    gap: 10px;
    height: 100%;
    padding: 10px;
    border: var(--bg-color-primary-light) solid 2px;
    border-radius: 5px;
    background-color: var(--bg-color-secondary);
}

.note-container{
    display: inline-block;
    width: 100%;
    .note{
        display: flex;
        flex-direction: row;
        padding: 0.5em;
        border: var(--bg-color-primary-light) solid 2px;
        border-radius: 5px;
        background-color: var(--bg-color-secondary-light);
        color: var(--color-grey);
        transition: all 0.3s;
        font-family: 'Roboto Mono', monospace;

        &__title{
            border-right: var(--bg-color-primary-light) solid 2px;
            padding-right: 0.5em;
            margin-right: 0.5em;
        }
        &__text{
            margin-top: 1em;
        }
    }
    .note:hover{
        background-color: var(--bg-color-black-light);
    }
}

.modal__container{
    display: none;
    justify-content: center;
    align-items: center;
    position:fixed;
    width: 100%;
    height: 100%;
    top: 50%;
    left: 50%;
    transform: translate(-50%,-50%);
    font-family: 'Roboto Mono', monospace;
    background-color: var(--bg-color-black-light--05);
}
.modal{
    display: flex;
    flex: 1;
    flex-direction: column;
    gap: 10px;
    width: 100%;
    max-width: 400px;
    height: max-content;
    padding: 10px;
    color: var(--color-grey);
    border: var(--bg-color-primary-light) solid 2px;
    border-radius: 5px;
    background-color: var(--bg-color-secondary-light);

    &__header{
        padding: 10px;
        border-bottom: var(--bg-color-primary-light) solid 2px;

        .modal__title{
            text-align: center;
        }
    }
    &__options{
        display: flex;
        flex-direction: row;
        justify-content: space-between;

        .modal__button{
            width: max-content;
            padding: 0.5em;
            outline: none;
            border: none;
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

}

</style>