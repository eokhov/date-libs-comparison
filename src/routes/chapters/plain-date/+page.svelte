<script>
  import { Temporal } from "temporal-polyfill";
  import DemoTable from "$lib/components/DemoTable.svelte";

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
            call: "plainDate.toString()",
            output: plainDate.toString(),
            description: "Получение полной даты ISO",
          },
          {
            call: "plainDate.toLocaleString()",
            output: plainDate.toLocaleString('ru-RU', {weekday: 'long', year: 'numeric', day: '2-digit'}),
            description: "Получить даты в формате региона",
          },
          {
            call: "plainDate.dayOfWeek",
            output: plainDate.dayOfWeek,
            description: "Получить номер дня недели",
          },
          {
            call: "plainDate.daysInWeek",
            output: plainDate.daysInWeek,
            description: "Получить количество дней в неделе",
          },
          {
            call: "plainDate.daysInMonth",
            output: plainDate.daysInMonth,
            description: "Получить количество дней в месяце",
          },
          {
            call: "plainDate.daysInYear",
            output: plainDate.daysInYear,
            description: "Получить количество дней в году",
          },
          {
            call: "plainDate.dayOfYear",
            output: plainDate.dayOfYear,
            description: "Получить номер дня в году",
          },
          {
            call: "plainDate.weekOfYear",
            output: plainDate.weekOfYear,
            description: "Получить номер недели в году",
          },
          {
            call: "plainDate.monthsInYear",
            output: plainDate.monthsInYear,
            description: "Получить количество месяцев в году",
          },
          {
            call: "plainDate.inLeapYear",
            output: plainDate.inLeapYear,
            description: "Узнать високосный год или нет",
          },
        ]}
      />
    </div>
    <div class="demo-text">
      <h1>PlainDate</h1>

      <p class="date-representation"><b class="current-scope">2024-11-01</b>T23:13:07+09:00</p>
    </div>
  </div>
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
