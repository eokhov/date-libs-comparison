<script>
  import { Temporal } from "temporal-polyfill";
  import { format, sub } from "date-fns";
  import { TZDate } from "@date-fns/tz";
  import DemoContainer from "$lib/components/DemoContainer.svelte";

  const serverDateTimeISO = '2024-11-18T11:10:13+03:00';
  const {timeZoneId} = Temporal.Now.zonedDateTimeISO();

  const zonedInstant = Temporal.Instant.from(serverDateTimeISO).toZonedDateTimeISO(timeZoneId);
  const tzDate = new TZDate(serverDateTimeISO, timeZoneId);

  const plainDateTime = Temporal.PlainDateTime.from(serverDateTimeISO);
  const tzDateMsk = new TZDate(serverDateTimeISO, 'Europe/Moscow');
</script>

<section>
  <div class="top-block">
    <div class="demo-interactive">
    </div>
    <div class="demo-text">
      <h1>ZonedDateTime</h1>

      <p class="date-representation">
        <b class="current-scope">2024-11-01T23:13:07+09:00[Asia/Tokyo]</b>
      </p>
    </div>
  </div>
  <div>
    <h3>Пример #1</h3>
    <p>Получаем дату в ISO формате, <i>{serverDateTimeISO}</i> в часом поясе <i>+03:00['Europe/Moscow']</i>,
      нужно отображать и оперировать в часовой поясе пользователя</p>
    <DemoContainer title="Вариант с Temporal">
      <pre>// Получаем часовой пояс пользователя</pre>
      <code>const timeZoneId = Temporal.Now.zonedDateTimeISO().timeZoneId;</code>
      <pre>// Преобразовываем исходную дату в часовой пояс пользователя</pre>
      <code>const zonedInstant = Temporal.Instant.from({serverDateTimeISO}+03:00).toZonedDateTimeISO(timeZoneId);</code>
      <pre>// Теперь с этим объектом можно взаимодействовать, например отобразить дату полностью</pre>
      <code>zonedInstant.toPlainDateTime().toString() -> {zonedInstant.toPlainDateTime().toString()}</code>
      <pre>// Или  например добавить несколько часов</pre>
      <code>zonedInstant.add({'{hours: 2}'}) -> {zonedInstant.add({hours: 2}).toPlainDateTime().toString()}</code>
      <pre>// Узнать день недели</pre>
      <code>zonedInstant.dayOfWeek -> {zonedInstant.dayOfWeek} // означает понедельник</code>
    </DemoContainer>
    <DemoContainer title="Вариант с @date-fns/tz">
      <pre>// Чтобы создать объект даты с которой можно работать в конструктор TZDate передаем исходную дату и часовой пояс</pre>
      <pre>// Библиотека @date-fns/tz не имеет встроенной функции для получения текущего часового пояса</pre>
      <pre>// поэтому воспользуемся переменной из примера с Temporal</pre>
      <code>const tzDate = new TZDate(serverDateTimeISO, timeZoneId);</code>
      <pre>// Теперь можем применить форматирование к этой дате</pre>
      <code>format(tzDate, 'yyyy-MM-dd HH:mm:ss'); -> {format(tzDate, 'yyyy-MM-dd HH:mm:ss')}</code>
      <pre>// Или применять другие функции из библиотеки date-fns</pre>
      <code>sub(tzDate, {'{days: 2}'}); -> {sub(tzDate, {days: 2}).toString()}</code>
    </DemoContainer>
  </div>
  <div>
    <h3>Пример #2</h3>
    <p>Получаем дату в ISO формате, <i>{serverDateTimeISO}</i> в часом поясе <i>+03:00['Europe/Moscow']</i>,
      нужно отображать и оперировать независимо от часового пояса пользователя</p>
    <DemoContainer title="Вариант с Temporal">
      <pre>// Для создания объекта даты можно к примеру воспользоваться классом PlainDateTime</pre>
      <code>const plainDateTime = Temporal.PlainDateTime.from(serverDateTimeISO);</code>
      <pre>// Теперь с этим объектом можно взаимодействовать, например отобразить дату полностью</pre>
      <code>plainDateTime.toString() -> {plainDateTime.toString()}</code>
      <pre>// Или получить месяц</pre>
      <code>plainDateTime.monthCode -> {plainDateTime.month}</code>
      <pre>// Так же можно перевести дату к другим типам например: <i>ZonedDateTime, PlainDate, PlainTime</i></pre>
      <code>plainDateTime.plainDateTime() -> {plainDateTime.toPlainTime()}</code>
    </DemoContainer>
    <DemoContainer title="Вариант с @date-fns/tz">
      <pre>// Чтобы создать дату с помощью TZDate в конструктор нужно явно передать часовой пояс к которому относиться дата</pre>
      <code>const tzDate = new TZDate(serverDateTimeISO, 'Europe/Moscow');</code>
      <pre>// Теперь можем применить форматирование к этой дате</pre>
      <code>format(tzDateMsk, 'yyyy-MM-dd HH:mm:ss'); -> {format(tzDateMsk, 'yyyy-MM-dd HH:mm:ss')}</code>
      <pre>// Или применять другие функции из библиотеки date-fns</pre>
      <code>sub(tzDateMsk, {'{hours: 7, minutes: 4}'}); -> {sub(tzDateMsk, {hours: 7, minutes: 4}).toString()}</code>
    </DemoContainer>
  </div>
</section>

<style>
  pre {
    margin-bottom: 0;
  }
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
