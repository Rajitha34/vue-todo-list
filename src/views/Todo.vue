<template>
  <div class="home">
    <v-text-field
      v-model="newTaskTitle"
      @click:append-outer="addTask"
      @keyup.enter="addTask"
      class="pa-3"
      outlined
      label="I want to...."
      append-outer-icon="mdi-plus-circle "
      color="teal"
      hide-details
      clearable
    ></v-text-field>
    <v-menu
      :close-on-content-click="false"
      transition="scale-transition"
      offset-y
    >
      <template v-slot:activator="{ on, attrs }">
        <v-btn
          v-bind="attrs"
          v-on="on"
          class="teal white--text"
          absolute
          center
          :style="{ left: '90%', trasform: 'translatex(-95%)' }"
        >
          calendar
        </v-btn>
      </template>
      <v-date-picker v-model="date" no-title></v-date-picker>
    </v-menu>
    <h2 class="pl-5">TODAY</h2>

    <v-list flat>
      <div v-for="task in tasks" :key="task.id">
        <v-list-item
          v-if="task.date == getTodaydate()"
          @click="doneTask(task.id)"
          :class="{ 'blue lighten-5': task.done }"
        >
          <template v-slot:default>
            <v-list-item-action>
              <v-checkbox :input-value="task.done" color="teal"></v-checkbox>
            </v-list-item-action>

            <v-list-item-content>
              <v-list-item-title
                :class="{ 'text-decoration-line-through': task.done }"
              >
                {{ task.title }}
              </v-list-item-title>
            </v-list-item-content>
            <v-list-item-action>
              <v-btn @click.stop="deleteTask(task.id)" icon>
                <v-icon color="teal">mdi-delete</v-icon>
              </v-btn>
            </v-list-item-action>
          </template>
        </v-list-item>
      </div>
    </v-list>
    <h2 class="pl-5">TOMORROW</h2>
    <v-list flat>
      <div v-for="task in tasks" :key="task.id">
        <v-list-item
          v-if="task.date == getTomorrowdate()"
          @click="doneTask(task.id)"
          :class="{ 'blue lighten-5': task.done }"
        >
          <template v-slot:default>
            <v-list-item-action>
              <v-checkbox :input-value="task.done" color="teal"></v-checkbox>
            </v-list-item-action>

            <v-list-item-content>
              <v-list-item-title
                :class="{ 'text-decoration-line-through': task.done }"
              >
                {{ task.title }}
              </v-list-item-title>
            </v-list-item-content>
            <v-list-item-action>
              <v-btn @click.stop="deleteTask(task.id)" icon>
                <v-icon color="teal">mdi-delete</v-icon>
              </v-btn>
            </v-list-item-action>
          </template>
        </v-list-item>
      </div>
    </v-list>
    <h2 class="pl-5">UPCOMING</h2>
    <v-list flat>
      <div v-for="task in tasks" :key="task.id">
        <v-list-item
          v-if="task.date == getUpcomingdate()"
          @click="doneTask(task.id)"
          :class="{ 'blue lighten-5': task.done }"
        >
          <template v-slot:default>
            <v-list-item-action>
              <v-checkbox :input-value="task.done" color="teal"></v-checkbox>
            </v-list-item-action>

            <v-list-item-content>
              <v-list-item-title
                :class="{ 'text-decoration-line-through': task.done }"
              >
                {{ task.title }}
              </v-list-item-title>
            </v-list-item-content>
            <v-list-item-action>
              <v-btn @click.stop="deleteTask(task.id)" icon>
                <v-icon color="teal">mdi-delete</v-icon>
              </v-btn>
            </v-list-item-action>
          </template>
        </v-list-item>
      </div>
    </v-list>
    <h2 class="pl-5">SOMEDAY</h2>
    <v-list flat>
      <div v-for="task in tasks" :key="task.id">
        <v-list-item
          v-if="task.date == getSomedaydate()"
          @click="doneTask(task.id)"
          :class="{ 'blue lighten-5': task.done }"
        >
          <template v-slot:default>
            <v-list-item-action>
              <v-checkbox :input-value="task.done" color="teal"></v-checkbox>
            </v-list-item-action>

            <v-list-item-content>
              <v-list-item-title
                :class="{ 'text-decoration-line-through': task.done }"
              >
                {{ task.title }}
              </v-list-item-title>
            </v-list-item-content>
            <v-list-item-action>
              <v-btn @click.stop="deleteTask(task.id)" icon>
                <v-icon color="teal">mdi-delete</v-icon>
              </v-btn>
            </v-list-item-action>
          </template>
        </v-list-item>
      </div>
    </v-list>
  </div>
</template>

<script>
export default {
  name: "Home",
  data() {
    return {
      newTaskTitle: "",
      date: "",
      tasks: [],
    };
  },
  methods: {
    addTask() {
      console.log(this.date);

      let newTask = {
        id: Date.now(),
        title: this.newTaskTitle,
        date: this.date,
        done: false,
      };
      this.tasks.push(newTask);
      this.newTaskTitle = "";
      localStorage.setItem("tasks", JSON.stringify(newTask));
    },

    doneTask(id) {
      let task = this.tasks.filter((task) => task.id === id)[0];
      task.done = !task.done;
    },
    deleteTask(id) {
      this.tasks = this.tasks.filter((task) => task.id !== id);
    },
    getTodaydate() {
      let d = new Date();
      return d.toISOString().split("T")[0];
    },
    getTomorrowdate() {
      let d = new Date();
      d.setDate(d.getDate() + 1);
      return d.toISOString().split("T")[0];
    },
    getUpcomingdate() {
      let d = new Date();
      d.setDate(d.getDate() + 5);
      return d.toISOString().split("U")[0];
    },
    getSomedaydate() {
      let d = new Date();
      d.setDate(d.getDate() + 10);
      return d.toISOString().split("S")[0];
    },
  },
};
</script>
