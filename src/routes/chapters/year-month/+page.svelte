<script>
  import { Temporal } from "temporal-polyfill";
  import { getYear, getMonth, getDaysInMonth, getDaysInYear } from "date-fns";
  import DemoTable from "$lib/components/DemoTable.svelte";
  import Section from "$lib/components/Section.svelte";

  const currentDate = Temporal.Now.plainDateISO().toString();

  let plainDate = $state(Temporal.PlainDate.from(currentDate));

  const handleChange = (event) => {
    plainDate = Temporal.PlainDate.from(event.target.value);
  };
</script>

<section>
  <div class="top-block">
    <div class="demo-interactive">
      <div class="date-selector">
        <label for="calendar">Выбери дату</label>
        <input
          type="date"
          name="calendar"
          id="calendar"
          value={plainDate.toString()}
          onchange={handleChange}
        />
      </div>
      <DemoTable
        data={[
          {
            call: "plainYearMonth.toString()",
            output: plainDate.toPlainYearMonth().toString(),
            description: "Получение полной даты ISO",
          },
          {
            call: "plainYearMonth.year",
            output: plainDate.toPlainYearMonth().year,
            description: "Получить текущий год",
          },
          {
            call: "plainYearMonth.month",
            output: plainDate.toPlainYearMonth().month,
            description: "Получить текущий месяц",
          },
          {
            call: "plainYearMonth.add({ years: 2 })",
            output: plainDate.toPlainYearMonth().add({ years: 2 }).toString(),
            description: "Прибавить 2 года к дате",
          },
          {
            call: "plainYearMonth.add({ months: 5 })",
            output: plainDate.toPlainYearMonth().add({ months: 5 }).toString(),
            description: "Прибавить 5 месяцев к дате",
          },
          {
            call: "plainYearMonth.subtract({ years: 3 })",
            output: plainDate
              .toPlainYearMonth()
              .subtract({ years: 3 })
              .toString(),
            description: "Вычесть 3 года из даты",
          },
          {
            call: "plainYearMonth.subtract({ months: 1 })",
            output: plainDate
              .toPlainYearMonth()
              .subtract({ months: 1 })
              .toString(),
            description: "Вычесть 1 месяц из даты",
          },
          {
            call: "plainYearMonth.with({ year: 2028 })",
            output: plainDate
              .toPlainYearMonth()
              .with({ year: 2028 })
              .toString(),
            description: "Установить год даты",
          },
          {
            call: "plainYearMonth.with({ month: 1 })",
            output: plainDate.toPlainYearMonth().with({ month: 1 }).toString(),
            description: "Установить месяц даты",
          },
          {
            call: "plainYearMonth.until('2025-01')",
            output: plainDate.toPlainYearMonth().until("2025-01").toString(),
            description: "Рассчитать период ДО определенной даты",
          },
          {
            call: "plainYearMonth.since('2024-01')",
            output: plainDate.toPlainYearMonth().since("2024-01").toString(),
            description: "Рассчитать период ОТ определенной даты",
          },
          {
            call: "plainYearMonth.equals('2024-09')",
            output: plainDate.toPlainYearMonth().equals("2024-09").toString(),
            description: "Сравнить даты",
          },
        ]}
      />
    </div>
    <div class="demo-text">
      <h1>PlainYearMonth</h1>

      <p class="date-representation">
        <b class="current-scope">2024-11</b>-01T23:13:07+09:00
      </p>
    </div>
  </div>

  <Section
    title="Получение разных частей даты от текущего времени"
    tableHead={["Цель", "Temporal", "Date-fns"]}
    tableBody={[
      {
        description: "Получить год из даты",
        temporal: {
          call: "plainYearMonth.year",
          output: plainDate.toPlainYearMonth().year,
        },
        dateFns: {
          call: "getYear(new Date())",
          output: getYear(new Date()),
        },
      },
      {
        description: "Получить месяц из даты",
        temporal: {
          call: "plainYearMonth.month",
          output: plainDate.toPlainYearMonth().month,
        },
        dateFns: {
          call: "getMonth(new Date()) + 1",
          output: getMonth(new Date()) + 1,
        },
      },
      {
        description: "Получить количество дней в месяце из даты",
        temporal: {
          call: "plainYearMonth.month",
          output: plainDate.toPlainYearMonth().daysInMonth,
        },
        dateFns: {
          call: "getDaysInMonth(new Date())",
          output: getDaysInMonth(new Date()),
        },
      },
      {
        description: "Получить количество дней в году из даты",
        temporal: {
          call: "plainYearMonth.month",
          output: plainDate.toPlainYearMonth().daysInYear,
        },
        dateFns: {
          call: "getDaysInYear(new Date())",
          output: getDaysInYear(new Date()),
        },
      },
    ]}
  />
</section>

<style>
  .top-block {
    display: grid;
    grid-template-columns: 1fr 1fr;
    column-gap: 18px;
    padding-block-end: 20px;
    border-bottom: 1px solid #2e2e32;
  }
  .demo-interactive {
    display: flex;
    flex-direction: column;
    row-gap: 12px;
    margin-block-start: 102px;
  }
  .date-selector {
    display: flex;
    flex-direction: column;
    align-items: start;
    row-gap: 4px;
  }

  .date-representation {
    font-size: 2em;
    color: var(--text-light-secondary);
  }
  .current-scope {
    color: var(--accent);
  }

  @media (prefers-color-scheme: light) {
    .date-representation {
      color: var(--text-dark-secondary);
    }
  }
</style>
