<template>
  <div class="timetable">
    <div class="timetable__cont">
      <p v-for="(day, index) in currentWeeekArray" @click="toggleActive(index)">
        {{ day }}
      </p>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      currentWeeekArray: [],
    };
  },
  mounted() {
    this.currentDay();
  },
  methods: {
    currentDay() {
      let curr = new Date();
      for (let i = 0; i <= 5; i++) {
        let first = curr.getDate() - curr.getDay() + i;
        let day = new Date(curr.setDate(first)).toISOString().slice(0, 10);
        this.currentWeeekArray.push(new Date(day).getDate());
      }
    },
    toggleActive(index){
    }
  },
};
</script>
<style lang="scss">
.timetable {
  position: fixed;
  bottom: 10px;
  left: 0;

  width: 95%;
  height: 3rem;
  margin-left: 2.5%;

  background-color: #333;
  border-radius: 100px;
  color: #ffffff;
  font-weight: 600;
  box-shadow: rgba(100, 100, 111, 0.2) 0px 7px 29px 0px;

  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;

  &__cont {
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: space-between;
    height: 100%;
    width: 80%;

    p {
      font-size: 0.7rem;
      margin: 0;

      width: 1.5rem;
      height: 1.5rem;
      
      border-radius: 10px;

      display: flex;
      flex-direction: row;
      align-items: center;
      justify-content: center;

      &.active {
        background-color: rgba(255, 255, 255, 0.301);
      }

      &:first-child {
        position: relative;

        &::after {
          content: "";
          width: 3px;
          height: 3px;
          background-color: #fff;

          position: absolute;
          bottom: -5px;
          left: 42.5%;
        }
      }
    }
  }
}
</style>
