<script>
  import {
    getDate,
    getDay,
    getDaysInMonth,
    getDaysInYear,
    getDayOfYear,
    getMonth,
    getYear,
    getHours,
    getMinutes,
  } from "date-fns";
  import { Temporal } from "temporal-polyfill";
  import Section from "$lib/components/Section.svelte";
</script>

<Section
  title="Получение разных частей даты от текущего времени"
  tableHead={["Цель", "Temporal", "Date-fns", "Date"]}
  tableBody={[
    {
      description: "Получить текущий год",
      temporal: {
        call: "Temporal.Now.plainDateISO().year",
        output: Temporal.Now.plainDateISO(),
      },
      dateFns: {
        call: "getYear(new Date())",
        output: getYear(new Date()),
      },
      dateJs: {
        call: "new Date().getFullYear()",
        output: new Date().getFullYear(),
      },
    },
    {
      description: "Получить число месяца",
      temporal: {
        call: "Temporal.Now.plainDateISO().day",
        output: Temporal.Now.plainDateISO().day,
      },
      dateFns: {
        call: "getDate(new Date())",
        output: getDate(new Date()),
      },
      dateJs: {
        call: "new Date().getDate()",
        output: new Date().getDate(),
      },
    },
    {
      description: "Получить текущий месяц",
      temporal: {
        call: "Temporal.Now.plainDateISO().month",
        output: Temporal.Now.plainDateISO().month,
      },
      dateFns: {
        call: "getMonth(new Date()) + 1",
        output: getMonth(new Date()) + 1,
      },
      dateJs: {
        call: "new Date().getMonth() + 1",
        output: new Date().getMonth() + 1,
      },
    },
    {
      description: "Получить текущий час",
      temporal: {
        call: "Temporal.Now.plainTimeISO().hour",
        output: Temporal.Now.plainTimeISO().hour,
      },
      dateFns: {
        call: "getHours(new Date())",
        output: getHours(new Date()),
      },
      dateJs: {
        call: "new Date().getHours()",
        output: new Date().getHours(),
      },
    },
    {
      description: "Получить текущую минуту",
      temporal: {
        call: "Temporal.Now.plainTimeISO().minute",
        output: Temporal.Now.plainTimeISO().minute,
      },
      dateFns: {
        call: "getMinutes(new Date())",
        output: getMinutes(new Date()),
      },
      dateJs: {
        call: "new Date().getMinutes()",
        output: new Date().getMinutes(),
      },
    },
    {
      description: "Получить количество дней в месяце",
      temporal: {
        call: "Temporal.Now.plainDateISO().daysInMonth",
        output: Temporal.Now.plainDateISO().daysInMonth,
      },
      dateFns: {
        call: "getDaysInMonth(new Date())",
        output: getDaysInMonth(new Date()),
      },
      dateJs: {
        call: "new Date(year, month, date).getDate()",
        output: new Date(
          new Date().getFullYear(),
          new Date().getMonth() + 1,
          0
        ).getDate(),
      },
    },
    {
      description: "Получить количество дней в году",
      temporal: {
        call: "Temporal.Now.plainDateISO().daysInYear",
        output: Temporal.Now.plainDateISO().daysInYear,
      },
      dateFns: {
        call: "getDaysInYear(new Date())",
        output: getDaysInYear(new Date()),
      },
      dateJs: {
        call: "Custom function",
        output: "",
      },
    },
    {
      description: "Получить день в году",
      temporal: {
        call: "Temporal.Now.plainDateISO().dayOfYear",
        output: Temporal.Now.plainDateISO().dayOfYear,
      },
      dateFns: {
        call: "getDayOfYear(new Date())",
        output: getDayOfYear(new Date()),
      },
      dateJs: {
        call: "Custom function",
        output: "",
      },
    },
    {
      description: "Получить день недели",
      temporal: {
        call: "Temporal.Now.plainDateISO().dayOfWeek",
        output: Temporal.Now.plainDateISO().dayOfWeek,
      },
      dateFns: {
        call: "getDay(new Date())",
        output: getDay(new Date()),
      },
      dateJs: {
        call: "new Date().getDay()",
        output: new Date().getDay(),
      },
    },
  ]}
/>
