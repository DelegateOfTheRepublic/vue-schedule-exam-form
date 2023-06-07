<template>
  <div id="app" class="main">
    <exam-item :examData="examData" />
    <exam-item :newMode="'edit'" />
  </div>
</template>

<script>
import ExamItem from "./components/ExamItem";

export default {
  name: "App",
  components: {
    ExamItem,
  },
  data() {
    return {
      examData: {
        studyGroup: "ПИ-4ИВТ186А",
        subject: "Нейроинформатика",
        teacher: "Полупанов",
        consultTime: "23:43",
        consultDate: "2023-06-07",
        consultRoom: "521",
        examTime: "23:44",
        examDate: "2023-07-07",
        examRoom: "501",
      },
    };
  },
};
</script>

<style>
* {
  box-sizing: border-box;
}

body {
  margin: 0;
  width: 100%;
  min-height: 100vh;
  overflow: auto;
}

ul {
  margin: 0;
  padding: 0;
}

li {
  list-style-type: none;
}

p {
  margin: 0;
}

.main {
  width: 100%;
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 50px;
}
</style>
