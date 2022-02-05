# CV by Artem Shabanov
## _🚀Junior frontend developer_

##### Hi. My name is Artem Shabanov, a.k.a. Artsiom Shabanau _( as in the passport )_.

The main thing I do now at my job is the development of new functionality and layout. Due to the nature of the business, I make this functionality for a specific CMS, using its API, so these solutions are not entirely applicable from the outside, but they give a general idea of the work of algorithms and the sequence of actions for solving such problems. I'm going to remake one project in the near future from just a bunch of HTML pages to Node.js + Vue.js.

My straights are a sense of humor, the ability to manage working time, sociability, I'm always responsible for words, hard-working _( but sometimes I can say it's a weakness )_. Fast-learner, able to work independently, quality-oriented.

Now I have 2 lessons per week for English and my level is between __B1__ and __B2__ by course program. By the way, I study Lithuanian, also 2 times a week.

## 📞Contacts

| Type | Detail |
| ------ | ------ |
| [Telegram](https://t.me/temashabanov) | @temashabanov |
| [E-mail](mailto:itemashabanov@gmail.com) | itemashabanov@gmail.com |
| [Phone](tel:+37067840337) | +370 - (678) - 40 - 337 |

## 🗿What about my skills

- HTML 5
- CSS 3
- Adaptive and responsive layouts
- SASS
- BEM
- JS
- jQuery
- TypeScript
- 1C-Bitrix _(sorry)_

## 👨🏻‍🎓Education

> __2015 – 2019__ \| Minsk Innovation Univercity, Information technology software, bachelor.

> __2019 – 2020__ \| Minsk Innovation Univercity, Computer science and programming technologies, master degree, but for some reason I had to take my documents

> __Spring 2021__ \| Has completed the program "Vue.js course". From 04.03.2021 to 11.04.2021

> __Winter 2021 and now__ \| Now I'm taking a "Node.js" course.

## 📈Expirience

I work for a company that sells cash registers and all that I do is the creation of new functionality, pages layout, maintenance of modules, refactoring of old code. I work here since 2019.
In-text above I wrote, that I ended the Vue course, and it's a [repo with its source code](https://github.com/itemashabanov/vue-20210304_itemashabanov).

You can also look at the process of creating an online store of my company on Vue.js [here](https://github.com/itemashabanov/spb-kassa).

## 🛠 This is the example of my last code

<details>
  <summary>Vue.js component for meetaps calendar</summary>
  <p>

  ```vue
    <template>
      <div class="rangepicker">
        <div class="rangepicker__calendar">
          <div class="rangepicker__month-indicator">
            <div class="rangepicker__selector-controls">
              <button class="rangepicker__selector-control-left" @click="decrease"></button>
              <div>{{ localeDate }}</div>
              <button class="rangepicker__selector-control-right" @click="increase"></button>
            </div>
          </div>
          <div class="rangepicker__date-grid">
            <div v-for="day in prevMonthDays" class="rangepicker__cell rangepicker__cell_inactive">
              {{ day.day }}
              <a v-for="meetup in day.meetups" class="rangepicker__event">{{ meetup.title }}</a>
            </div>
            <template v-for="week in curMonthDays">
              <div v-for="day in week" class="rangepicker__cell">
                {{ day.day }}
                <a v-for="meetup in day.meetups" class="rangepicker__event">{{ meetup.title }}</a>
              </div>
            </template>
            <div v-for="day in nextMonthDays" class="rangepicker__cell rangepicker__cell_inactive">
              {{ day.day }}
              <a v-for="meetup in day.meetups" class="rangepicker__event">{{ meetup.title }}</a>
            </div>
          </div>
        </div>
      </div>
    </template>

    <script>
    export default {
      name: 'MeetupsCalendar',

      props: {
        meetups: {
          type: Array,
          required: true,
        },
      },

      data() {
        return {
          date: new Date(),
        };
      },

      computed: {
        localeMeetups() {
          if (!this.meetups) return false;

          return this.meetups.map((meetup) => ({
            ...meetup,
            year: new Date(meetup.date).getFullYear(),
            month: new Date(meetup.date).getMonth(),
            day: new Date(meetup.date).getDate(),
          }));
        },

        month() {
          return this.date.getMonth()
        },

        year() {
          return this.date.getFullYear()
        },

        localeDate() {
          return this.date.toLocaleString(navigator.language, {
            year: 'numeric',
            month: 'long',
          });
        },

        prevMonthDays() {
          const prevMonth = new Date(this.year, this.month, 0).getDate();
          let days = [];
          if (this.curMonthDays[0].length > 0) {
            for (let i = this.curMonthDays[0].length; i < 7; i++) {
              const meetups = this.filterMeetups(prevMonth - 6 + i, this.month, this.year);
              days.push({ day: prevMonth - 6 + i, meetups });
            }
          }
          return days;
        },

        nextMonthDays() {
          let days = [];
          if (this.curMonthDays[this.curMonthDays.length - 1].length > 0) {
            for (let i = this.curMonthDays[this.curMonthDays.length - 1].length, j = 1; i < 7; i++, j++) {
              const meetups = this.filterMeetups(i, this.month, this.year);
              days.push({ day: j, meetups });
            }
          }
          return days;
        },

        curMonthDays() {
          let days = [],
            week = 0;
          const thisMonthDays = new Date(this.year, this.month + 1, 0).getDate();

          days[week] = [];
          for (let i = 1; i <= thisMonthDays; i++) {
            const meetups = this.filterMeetups(i, this.month, this.year);
            if (new Date(this.year, this.month, i).getDay() != 1) {
              days[week].push({ day: i, meetups });
            } else {
              week++;
              days[week] = [];
              days[week].push({ day: i, meetups });
            }
          }
          return days;
        },
      },

      methods: {
        decrease() {
          this.date = new Date(this.year, this.month - 1);
        },

        increase() {
          this.date = new Date(this.year, this.month + 1);
        },

        filterMeetups(day, month, year) {
          return this.localeMeetups.filter((meetup) => {
            return day === meetup.day && month === meetup.month && year === meetup.year;
          });
        },
      },
    };
    </script>
  ```

  </p>
</details>

## Thank you very much for reading! ✌🏼