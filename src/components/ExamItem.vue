<template>
  <div class="exam-item">
    <div class="wrapper">
      <div class="sign-add" v-if="!showInfo" @click="showInfo = true">
        <svg
          xmlns="http://www.w3.org/2000/svg"
          version="1.1"
          xmlns:xlink="http://www.w3.org/1999/xlink"
          xmlns:svgjs="http://svgjs.com/svgjs"
          width="16"
          height="16"
          x="0"
          y="0"
          viewBox="0 0 512 512"
          style="enable-background: new 0 0 512 512"
          xml:space="preserve"
          class=""
        >
          <g>
            <g data-name="03 Login">
              <path
                d="M256 512a25 25 0 0 1-25-25V25a25 25 0 0 1 50 0v462a25 25 0 0 1-25 25z"
                fill="#000000"
                data-original="#000000"
              ></path>
              <path
                d="M487 281H25a25 25 0 0 1 0-50h462a25 25 0 0 1 0 50z"
                fill="#000000"
                data-original="#000000"
              ></path>
            </g>
          </g>
        </svg>
      </div>
      <div class="sign-remove" v-if="showInfo" @click="hideInfo">
        <svg
          xmlns="http://www.w3.org/2000/svg"
          version="1.1"
          xmlns:xlink="http://www.w3.org/1999/xlink"
          xmlns:svgjs="http://svgjs.com/svgjs"
          width="16"
          height="16"
          x="0"
          y="0"
          viewBox="0 0 409.6 409.6"
          style="enable-background: new 0 0 512 512"
          xml:space="preserve"
          class=""
        >
          <g>
            <path
              d="M392.533 187.733H17.067C7.641 187.733 0 195.374 0 204.8s7.641 17.067 17.067 17.067h375.467c9.426 0 17.067-7.641 17.067-17.067s-7.642-17.067-17.068-17.067z"
              fill="#000000"
              data-original="#000000"
              class=""
            ></path>
          </g>
        </svg>
      </div>
      <div class="exam-item__short-info">
        {{ subject || "Новый экзамен" }}
      </div>
      <div
        class="edit"
        v-if="subject"
        @click="(mode = 'edit'), (showInfo = true)"
      >
        <svg
          xmlns="http://www.w3.org/2000/svg"
          version="1.1"
          xmlns:xlink="http://www.w3.org/1999/xlink"
          xmlns:svgjs="http://svgjs.com/svgjs"
          width="18"
          height="18"
          x="0"
          y="0"
          viewBox="0 0 401.523 401"
          style="enable-background: new 0 0 512 512"
          xml:space="preserve"
          class=""
        >
          <g>
            <path
              d="M370.59 250.973c-5.524 0-10 4.476-10 10v88.789c-.02 16.562-13.438 29.984-30 30H50c-16.563-.016-29.98-13.438-30-30V89.172c.02-16.559 13.438-29.98 30-30h88.79c5.523 0 10-4.477 10-10 0-5.52-4.477-10-10-10H50c-27.602.031-49.969 22.398-50 50v260.594c.031 27.601 22.398 49.968 50 50h280.59c27.601-.032 49.969-22.399 50-50v-88.793c0-5.524-4.477-10-10-10zm0 0"
              fill="#000000"
              data-original="#000000"
              class=""
            ></path>
            <path
              d="M376.629 13.441c-17.574-17.574-46.067-17.574-63.64 0L134.581 191.848a9.997 9.997 0 0 0-2.566 4.402l-23.461 84.7a9.997 9.997 0 0 0 12.304 12.308l84.7-23.465a9.997 9.997 0 0 0 4.402-2.566l178.402-178.41c17.547-17.587 17.547-46.055 0-63.641zM156.37 198.348 302.383 52.332l47.09 47.09-146.016 146.016zm-9.406 18.875 37.62 37.625-52.038 14.418zM374.223 74.676 363.617 85.28l-47.094-47.094 10.61-10.605c9.762-9.762 25.59-9.762 35.351 0l11.739 11.734c9.746 9.774 9.746 25.59 0 35.36zm0 0"
              fill="#000000"
              data-original="#000000"
              class=""
            ></path>
          </g>
        </svg>
      </div>
    </div>
    <div class="exam-item__info" v-if="showInfo">
      <div class="exam-item__info-header">
        <template v-if="mode === 'edit'">
          <select name="" id="" v-model="studyGroup">
            <option selected disabled value="null">Группа</option>
            <option value="ПИ-4ИВТ186А">ПИ-4ИВТ186А</option>
          </select>
          <select name="" id="" v-model="subject">
            <option selected disabled value="null">Дисциплина</option>
            <option value="Нейроинформатика">Нейроинформатика</option>
            <option value="Математический анализ">Математический анализ</option>
          </select>
          <select name="" id="" v-model="teacher">
            <option selected disabled value="null">Преподаватель</option>
            <option value="Полупанов">Полупанов</option>
            <option value="Башмаков">Башмаков</option>
          </select>
        </template>
        <template v-else>
          <p>{{ studyGroup }}</p>
          <p>{{ subject }}</p>
          <p>{{ teacher }}</p>
        </template>
      </div>
      <div class="exam-item__ce">
        <div class="exam-item__consult">
          <p class="exam-item__ce-header">Консультация</p>
          <template v-if="mode === 'edit'">
            <input type="time" name="" id="timepicker" v-model="consult.time" />
            <input type="date" name="" id="datepicker" v-model="consult.date" />
            <select name="" id="" v-model="consult.room">
              <option selected disabled value="null">Аудитория</option>
              <option value="521">521</option>
              <option value="501">501</option>
            </select>
          </template>
          <template v-else>
            <p id="timepicker">{{ consult.time || examData["consultTime"] }}</p>
            <p id="datepicker">{{ consult.date || examData["consultDate"] }}</p>
            <p id="room">{{ consult.room || examData["consultRoom"] }}</p>
          </template>
        </div>
        <div class="exam-item__exam">
          <p class="exam-item__ce-header">Экзамен</p>
          <template v-if="mode === 'edit'">
            <input type="time" name="" id="timepicker" v-model="exam.time" />
            <input type="date" name="" id="datepicker" v-model="exam.date" />
            <select name="" id="" v-model="exam.room">
              <option selected disabled value="null">Аудитория</option>
              <option value="521">521</option>
              <option value="501">501</option>
            </select>
          </template>
          <template v-else>
            <p id="timepicker">{{ exam.time || examData["examTime"] }}</p>
            <p id="datepicker">{{ exam.date || examData["examDate"] }}</p>
            <p id="room">{{ exam.room || examData["examRoom"] }}</p>
          </template>
        </div>
      </div>
      <div class="exam-item__btns" v-if="mode === 'edit'">
        <button @click="save">Сохранить</button>
        <button @click="cancel">Отмена</button>
      </div>
    </div>
  </div>
</template>

<script>
import _ from "lodash";

export default {
  props: {
    examData: {
      type: Object,
      default: () => {
        return {};
      },
    },
    newMode: {
      type: String,
      default: "view",
    },
  },
  data() {
    return {
      subject: this.$props.examData?.subject || null,
      studyGroup: this.$props.examData?.studyGroup || null,
      teacher: this.$props.examData?.teacher || null,
      consult: {
        time: this.$props.examData?.consultTime || "",
        date: this.$props.examData?.consultDate || "",
        room: this.$props.examData?.consultRoom || null,
      },
      exam: {
        time: this.$props.examData?.examTime || "",
        date: this.$props.examData?.examDate || "",
        room: this.$props.examData?.examRoom || null,
      },
      showInfo: false,
      mode: this.$props.newMode,
    };
  },
  methods: {
    cancel() {
      if (_.isEmpty(this.$props.examData)) {
        this.$emit("remove");
        return;
      }

      this.subject = this.$props.examData.subject;
      this.studyGroup = this.$props.examData.studyGroup;
      this.teacher = this.$props.examData.teacher;
      this.consult = {
        time: this.$props.examData.consultTime,
        date: this.$props.examData.consultDate,
        room: this.$props.examData.consultRoom,
      };
      this.exam = {
        time: this.$props.examData.examTime,
        date: this.$props.examData.examDate,
        room: this.$props.examData.examRoom,
      };
      this.mode = "view";
    },
    save() {},
    hideInfo() {
      if (_.isEmpty(this.$props.examData)) {
        this.$emit("remove");
        return;
      }

      this.showInfo = false;
      this.mode = "view";
    },
  },
};
</script>

<style scoped>
#timepicker:before {
  content: "Время:";
  margin-right: 0.6em;
  color: #9d9d9d;
}

#datepicker:before {
  content: "Дата:";
  margin-right: 0.6em;
  color: #9d9d9d;
}

#room:before {
  content: "Аудитория:";
  margin-right: 0.6em;
  color: #9d9d9d;
}

.exam-item {
  border: 2px solid gray;
  border-radius: 6px;
  height: fit-content;
}
.wrapper {
  display: flex;
  align-items: center;
  padding: 2px 6px;
}
.sign-add,
.sign-remove {
  display: flex;
  margin-right: 6px;
}
.sign-remove {
}
.edit {
  display: flex;
  margin-left: auto;
}
.sign-add,
.sign-remove,
.edit {
  cursor: pointer;
}
.exam-item__short-info {
  margin-right: 24px;
}
.exam-item__info {
  margin-top: 12px;
}
.exam-item__ce {
  display: flex;
  justify-content: space-between;
  padding: 0px 18px;
}
.exam-item__ce-header {
  margin-bottom: 6px;
  text-align: center;
}
.exam-item__consult,
.exam-item__exam {
  display: flex;
  flex-direction: column;
  padding: 12px;
}
.exam-item__info-header {
  display: flex;
  padding: 0px 30px;
  gap: 12px;
}
.exam-item__btns {
  display: flex;
  gap: 24px;
  justify-content: flex-end;
  margin: 12px 30px 12px 0px;
}
</style>