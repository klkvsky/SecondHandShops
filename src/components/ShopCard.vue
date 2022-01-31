<template>
  <div class="card">
    <div class="card__basicInfo">
      <h1>{{ itemData.name }}</h1>
      <p>{{ itemData.time }}</p>
       <p
        :class="{
          danger:
            itemData.schedule[getCurrentDate()].day === this.itemData.cicles,
        }"
        v-if="itemData.schedule[getCurrentDate()].discount != 0"
      >
        Скидка: {{ itemData.schedule[getCurrentDate()].discount }}%
      </p>
      <p v-else class="new">Новый завоз</p>
      <h4>{{ itemData.adress }}</h4>
    </div>
    <div class="card__reactiveInfo">
     

      <div class="card__reactiveInfo__icons">
        <span class="UnitOfSale">
          <svg
            width="20"
            height="20"
            viewBox="0 0 20 20"
            fill="none"
            xmlns="http://www.w3.org/2000/svg"
          >
            <path
              d="M4.99992 1.66669C4.99992 2.09419 5.40825 2.50002 5.83325 2.50002H14.1666C14.5941 2.50002 14.9999 2.09169 14.9999 1.66669H16.6666C16.6666 2.32973 16.4032 2.96561 15.9344 3.43445C15.4655 3.9033 14.8296 4.16669 14.1666 4.16669H10.8333L10.8341 5.88502C12.4449 6.08854 13.9262 6.87279 15 8.09066C16.0738 9.30854 16.6664 10.8764 16.6666 12.5V17.5C16.6666 17.721 16.5788 17.933 16.4225 18.0893C16.2662 18.2456 16.0543 18.3334 15.8333 18.3334H4.16659C3.94557 18.3334 3.73361 18.2456 3.57733 18.0893C3.42105 17.933 3.33325 17.721 3.33325 17.5V12.5C3.33328 10.8762 3.92591 9.30816 4.99992 8.09023C6.07393 6.8723 7.5555 6.08818 9.16658 5.88502V4.16669H5.83325C4.44992 4.16669 3.33325 3.05002 3.33325 1.66669H4.99992ZM9.99992 7.50002C7.30158 7.50002 4.99992 9.80002 4.99992 12.5V16.6667H14.9999V12.5C14.9999 9.80169 12.6983 7.50002 9.99992 7.50002ZM9.99992 9.16669C10.6183 9.16669 11.1966 9.33502 11.6933 9.62836L9.40992 11.9109C9.26046 12.0608 9.17369 12.2621 9.16723 12.4737C9.16077 12.6853 9.2351 12.8914 9.37513 13.0503C9.51515 13.2091 9.71038 13.3086 9.92115 13.3287C10.1319 13.3488 10.3424 13.2879 10.5099 13.1584L10.5891 13.0892L12.8724 10.8067C13.1713 11.313 13.3309 11.8894 13.3351 12.4773C13.3393 13.0652 13.1878 13.6438 12.8961 14.1543C12.6044 14.6648 12.1828 15.089 11.6741 15.3839C11.1655 15.6788 10.5879 15.8338 9.99992 15.8334C8.15825 15.8334 6.66658 14.3417 6.66658 12.5C6.66658 10.6584 8.15825 9.16669 9.99992 9.16669Z"
            />
          </svg>
        </span>
        <span class="isApplePayAviable">
          <svg
            width="16"
            height="18"
            viewBox="0 0 16 18"
            fill="none"
            xmlns="http://www.w3.org/2000/svg"
          >
            <path
              d="M12.2664 18C11.8937 17.8607 11.6276 17.5493 11.5655 17.1805C11.5211 16.9674 11.5655 16.8199 11.9204 16.2298C13.2511 14.017 13.9343 11.5174 13.8988 8.98505C13.9343 6.52643 13.2866 4.12517 12.0091 1.96978C11.8228 1.60918 11.6542 1.26497 11.5123 0.896181C11.5655 0.584755 11.7341 0.297916 12.0091 0.125812C12.4083 -0.0708775 12.8963 -0.0299005 13.26 0.199571C13.5084 0.494606 13.7214 0.78964 13.8988 1.13385C14.8534 2.82284 15.5036 4.64423 15.824 6.52643C16.0281 8.0098 16.0547 9.51775 15.9038 11.0093C15.6288 12.927 15.0167 14.7792 14.0762 16.5084C13.5084 17.5574 13.189 18 12.8519 18H12.2664ZM8.39821 16.1888C7.89251 16.0577 7.57312 15.5824 7.67959 15.107C7.67959 15.0087 7.95462 14.5579 8.20303 14.099C9.24992 12.2386 9.70238 10.1406 9.49833 8.05077C9.37412 6.55101 8.90391 5.09223 8.13206 3.77277C7.57312 2.74015 7.53764 2.57624 7.8659 2.13369C8.25626 1.73211 8.90391 1.67474 9.38299 2.01895C10.0218 2.88767 10.5275 3.83833 10.9001 4.83817C12.0357 7.94423 11.8583 11.3289 10.4033 14.3121C9.65802 15.861 9.13458 16.3609 8.39821 16.1478V16.1888ZM4.40585 14.3612C4.24788 14.2957 4.10775 14.1985 3.99569 14.0765C3.88364 13.9546 3.8025 13.8111 3.7582 13.6564C3.7582 13.4925 3.7582 13.2794 4.15744 12.6238C4.80781 11.5346 5.14891 10.3109 5.14891 9.067C5.14891 7.82308 4.80781 6.59942 4.15744 5.5102C3.58076 4.47757 3.58076 4.26449 4.05098 3.87111C4.21954 3.69082 4.46796 3.60067 4.73411 3.63345C5.30192 3.63345 5.6213 3.88751 6.10039 4.81359C6.85473 6.09298 7.24545 7.52822 7.23599 8.98505C7.27148 10.4684 6.88112 11.9436 6.10926 13.2467C5.63018 14.1072 5.39063 14.3121 4.91155 14.3858C4.74298 14.4022 4.56555 14.3858 4.40585 14.3121V14.3612ZM0.670777 12.6156C0.378004 12.4845 0.147334 12.2632 0.0319992 11.9764C-0.0567199 11.6895 0.0319993 11.4437 0.386876 10.9192C0.830471 10.3619 1.0434 9.67346 0.999038 8.98505C1.06114 8.28844 0.857087 7.60002 0.422363 7.02635C0.275109 6.81974 0.14463 6.60333 0.0319992 6.37891C-0.0655918 5.8626 0.307028 5.37087 0.91919 5.27253C1.39827 5.19058 1.73541 5.37907 2.179 6.00192C2.80841 6.88669 3.14379 7.92225 3.14379 8.98095C3.14379 10.0397 2.80841 11.0752 2.179 11.96C1.72653 12.591 1.21196 12.7795 0.679649 12.6156H0.670777Z"
            />
          </svg>
        </span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["itemData"],
  data() {
    return {
      name: "Мюнхен",
      workTime: "10:00 - 20:00",
      adress: "Уфа, улица Свердлова, 90",
      currentPrice: "250",
    };
  },
  methods: {
    getCurrentDate() {
      let nowDate = new Date();
      let firstDate = new Date(this.itemData.firstDay * 1000);

      let daysPassed = Math.abs(nowDate - firstDate);
      let fullDaysPassed = parseInt(daysPassed / (1000 * 3600 * 24));
      let fullCiclesSkiped =
        parseInt(fullDaysPassed) / parseInt(this.itemData.cicles);
      let currentDay =
        fullDaysPassed - parseInt(fullCiclesSkiped) * this.itemData.cicles;

      return currentDay;

      // return nowDate.getDate() + " " + firstDate.getDate();
      // var afterTwoWeeks = new Date(+firstDate + 1209600000);
      // const dateObject = new Date(1641150000*1000);
      // const humanDateFormat = dateObject.toString();
    },
  },
};
</script>

<style lang="scss">
.card {
  background-color: #fff;
  box-shadow: rgba(100, 100, 111, 0.2) 0px 7px 29px 0px;
  width: 90%;
  border-radius: 10px;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  padding: 3.5vw;

  @media (prefers-color-scheme: dark) {
    background-color: #212121;
    box-shadow: rgba(100, 100, 111, 0.15) 0px 7px 29px 0px;
  }

  //
  margin-bottom: 1rem;
  //

  &__basicInfo {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    justify-content: flex-start;
    gap: 1.5vw;

    h1 {
      font-size: 5vw;
      margin: 0;
      font-weight: 900;
    }
    p {
      font-size: 3vw;
      font-weight: 500;
      margin: 0;

      &.new {
        background-color: #90ee90;
        padding: 0.2rem 0.5rem;

        @media (prefers-color-scheme: dark) {
          color: #333;
        }
      }
      &.danger {
        background-color: #7c69ef;
        padding: 0.2rem 0.5rem;
        color: #fff;
      }
    }
    h4 {
      margin: 0;
      font-size: 3.2vw;
      font-weight: 400;
    }
  }

  &__reactiveInfo {
    display: flex;
    flex-direction: column;
    align-items: flex-end;
    justify-content: space-between;

    h1 {
      font-size: 3.5vw;
      margin: 0;
      font-weight: 900;
      border-radius: 5px;
    }

    &__icons {
      display: flex;
      flex-direction: row;
      justify-content: flex-end;
      gap: 3vw;
      width: 100%;

      svg {
        fill: black;

        @media (prefers-color-scheme: dark) {
          fill: #fff;
        }
      }
    }
  }
}

// Desktop Styles Archived for later
// .card {
//   background-color: #fff;
//   box-shadow: rgba(100, 100, 111, 0.2) 0px 7px 29px 0px;
//   max-width: 350px;
//   border-radius: 10px;
//   display: flex;
//   flex-direction: row;
//   justify-content: space-between;
//   padding: 1rem;

//   margin: 2rem;

//   &__basicInfo {
//     display: flex;
//     flex-direction: column;
//     align-items: flex-start;
//     justify-content: flex-start;
//     gap: .2rem;

//     h1 {
//       font-size: 1.5rem;
//       margin: 0;
//       font-weight: 900;
//     }
//     p {
//       font-size: .9rem;
//       font-weight: 500;
//       margin: 0;
//     }
//     h4 {
//       margin: 0;
//       font-size: 1rem;
//       font-weight: 400;
//     }
//   }

//   &__reactiveInfo {
//     display: flex;
//     flex-direction: column;
//     align-items: flex-end;
//     justify-content: space-between;

//     h1 {
//       font-size: 1.5rem;
//       margin: 0;
//       font-weight: 900;
//     }

//     &__icons {
//       display: flex;
//       flex-direction: row;
//       justify-content: space-between;
//       width: 50%;
//     }
//   }
// }
</style>
