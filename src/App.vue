<template>
  <h2>My Course Goal</h2>
  <!-- Task 1: Output your main course goal with help of the composition API -->
  <!-- Don't hardcode it into the template, instead hardcode it into the JS code -->
  <h3>{{ goal }}</h3>
  <h3>{{ reactiveGoal.filledGoal }}</h3>
  <!-- Task 2: Toggle (show/ hide) the goal with help of the button  -->
  <button @click="handleClick">Toggle Goal</button>
  <button @click="handleToggleReactiveGoals">Toggle Goal</button>
  <!-- Task 3: Manage data in three ways -->
  <!-- => Separate refs -->
  <!-- => Ref Object -->
  <!-- => Reactive Object -->
  <!-- Task 4: Also solve the assignment with the Options API -->
</template>

<script>
import { ref, reactive } from 'vue';
export default {
  //with refs
  setup() {
    const goal = ref(
      'My main goal is to master VueJs and build jawdropping apps :D'
    );

    const handleClick = () => {
      if (goal.value) {
        return (goal.value = '');
      } else if (goal.value === '') {
        return (goal.value =
          'My main goal is to master VueJs and build jawdropping apps :D');
      }
    };
    //with reactive
    const reactiveGoal = reactive({
      goal: 'My main goal is to master VueJs and build jawdropping apps :D',
      filledGoal: '',
      emptyGoal: '',
    });

    const handleToggleReactiveGoals = () => {
      reactiveGoal.filledGoal === ''
        ? (reactiveGoal.filledGoal = reactiveGoal.goal)
        : (reactiveGoal.filledGoal = reactiveGoal.emptyGoal);
    };
    return {
      goal,
      handleClick,
      reactiveGoal: reactiveGoal,
      handleToggleReactiveGoals,
    };
  },
  // with Options API
  // data() {
  //   return {
  //     courseGoal:
  //       'My main goal is to master VueJs and build jawdropping apps :D',
  //   };
  // },
  // methods: {
  //   toggleGoal() {
  //     if (this.courseGoal) {
  //       return (this.courseGoal = '');
  //     } else if (this.courseGoal === '') {
  //       return (this.courseGoal =
  //         'My main goal is to master VueJs and build jawdropping apps :D');
  //     }
  //   },
  // },
};
</script>

<style>
html {
  font-family: sans-serif;
}
body {
  margin: 3rem;
  text-align: center;
}
</style>
