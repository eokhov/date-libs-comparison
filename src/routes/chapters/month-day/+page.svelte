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
            call: "plainMonthDay.monthCode",
            output: plainDate.toPlainMonthDay().monthCode,
            description: "Получить текущий код месяца",
          },
          {
            call: "plainMonthDay.day",
            output: plainDate.toPlainMonthDay().day,
            description: "Получить текущий день",
          }
        ]}
      />
    </div>
    <div class="demo-text">
      <h1>PlainMonthDay</h1>
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
</style>
