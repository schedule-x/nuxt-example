<script setup>
import {ScheduleXCalendar} from "@schedule-x/vue";
import {
  createCalendar,
  viewDay,
  viewWeek,
  viewMonthGrid,
  viewMonthAgenda,
} from '@schedule-x/calendar'
import '@schedule-x/theme-default/dist/index.css'
import {createResizePlugin} from "@schedule-x/resize";
import {createScrollControllerPlugin} from "@schedule-x/scroll-controller";

const calendarApp = ref(createCalendar({
  selectedDate: '2023-12-19',
  views: [viewDay, viewWeek, viewMonthGrid, viewMonthAgenda],
  defaultView: viewWeek.name,
  plugins: [
      createResizePlugin(),
      createScrollControllerPlugin({
        initialScroll: '08:00'
      })
  ],
  events: [],
  calendars: {
    work: {
      colorName: 'work',
      lightColors: {
        container: '#fff',
        onContainer: '#000',
        main: '#fff',
      },
      darkColors: {
        container: '#000',
        onContainer: '#fff',
        main: '#000',
      },
    }
  }
}))

onMounted(() => {
  setTimeout(() => {
    calendarApp.value.events.set([
      {
        id: 1,
        title: 'Event 1',
        start: '2023-12-19',
        end: '2023-12-19',
      },
      {
        id: 2,
        title: 'Event 2',
        start: '2023-12-20 12:00',
        end: '2023-12-20 13:00',
      },
    ])
  }, 500)
})

</script>

<template>
  <div>
    <ClientOnly>
      <ScheduleXCalendar :calendar-app="calendarApp">
<!--        <template #timeGridEvent="{ calendarEvent }">-->
<!--          <div class="event">-->
<!--            {{ calendarEvent.title }}-->
<!--          </div>-->
<!--        </template>-->
      </ScheduleXCalendar>
    </ClientOnly>
  </div>
</template>

<style>
.sx-vue-calendar-wrapper {
  height: 700px;
  max-height: 90vh;
  width: 100%;
}
</style>
