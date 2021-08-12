<template>
  <div class="container">
    <v-app>
      <v-app-bar class="navbar" app>
        <v-app-bar-nav-icon @click="drawer = !drawer"><v-icon>mdi-reload</v-icon></v-app-bar-nav-icon>
        <v-toolbar-title>Habits Tracker</v-toolbar-title>
      </v-app-bar>
      <v-main>
    <v-row>
    <v-col>
      <v-sheet class="week" height="80" width="900">
        <v-calendar
          ref="calendar"
          color="primary"
          type="week"
        ></v-calendar>
      </v-sheet>
    </v-col>
  </v-row>
  <ul class="itens-container">
        <li v-for="(habit, atividade) in habits" :key="atividade" class="item">
        <label>{{ habit.atividade }}</label>
        <label class="porcent"> ({{ (habit.checked.length * 100 / 7).toFixed(0) }}%)</label>
        <span class="checkbox">
        <input class="check-item" type="checkbox" value="1" v-model="habit.checked">
        <input class="check-item" type="checkbox" value="2" v-model="habit.checked">
        <input class="check-item" type="checkbox" value="3" v-model="habit.checked">
        <input class="check-item" type="checkbox" value="4" v-model="habit.checked">
        <input class="check-item" type="checkbox" value="5" v-model="habit.checked">
        <input class="check-item" type="checkbox" value="6" v-model="habit.checked">
        <input class="check-item" type="checkbox" value="7" v-model="habit.checked">
        </span>
      </li>
  </ul>
      <input @keyup.enter="adicionarHabit" v-model="newHabit" type="text" class="inputhabit" />
      <span class="input-group-btn">
      <button @click="adicionarHabit" class="btn">
      Adicionar novo hábito
      </button>
      </span>
      </v-main>
    </v-app>
  </div>
</template>
       
<script>
  export default {
    name: "App",
    data() {
      return {
        newHabit: "",
        habits: [
            {atividade: "Ler 20 páginas", checked: []},
            {atividade: "Medicação", checked: []},
            {atividade: "Correr", checked: []},
            {atividade: "Dormir 8 horas", checked: []},
        ],
      }
    },
    methods: {
      adicionarHabit() {
        this.habits.push({
          atividade: this.newHabit,
          checked: [],
        })
        this.newHabit = "";
      },
    },
  }
</script>

<style scoped>
  .container {
    width: 80%;
    border: 1px solid rgba(128, 128, 128, 0.298);
  }
  .navbar {
    width: 69.800%;
    margin: 0 auto;
  }

   .week {
    position: absolute;
    right: 0;
    margin-top: 10px;
  }

  .itens-container {
    padding: 10px;
    margin-top: 6.9em;

  }

  .item {
    font-family: 'Segoe UI';
    font-size: 1.2em;
    list-style: none;
    margin-top: -0.4em;
    margin-bottom: 20px;
    padding: 20px;
    background: #eceff460;
    letter-spacing: 0.1em;
  }

  .porcent {
    color: red;
  }

  .checkbox {
    display: flex;
    justify-content: flex-end;
    margin-top: -1.5em;

    
  }

  li {
    margin-bottom: 20px;
  }

  .check-item {
    margin: 10px 50px 0 50px;

  }

  .inputhabit {
    background-color: #c5ccd84d;
    border-radius: 6px;
    margin: 0 10px 0 10px;
    
  }

  .btn {
    font-weight: bold;
    
  }

 
</style>