<script>
  import DemoContainer from "$lib/components/DemoContainer.svelte";
</script>

<section>
  <div class="top-block">
    <div class="demo-interactive"></div>
    <div class="demo-text">
      <h1>Duration</h1>
    </div>
  </div>
  <div>
    <h3>Temporal.Duration</h3>
    <p>
      Представляет собой промежуток времени, который может быть использован в
      арифметике с датой
    </p>
    <p>
      Чтобы создать объект типа Duration можно использовать конструктор или
      статический метод from()
    </p>
    <p>
      При использовании метода toString() мы получим строку формата ISO 8601.
      Если вкратце
      <b>ISO 8601</b> запись начинается с символа Р, следом идут год, месяц, неделя,
      день. Дальше может быть символ Т и следом за ним часы, минуты и секунды в виде
      чисел в десятичном представлении. Каждый из них имеет однобуквенный суффикс,
      обозначающий единицу измерения. Если какая либо секция будет 0, то она будет
      пропущена.
    </p>
    <DemoContainer title="Примеры создания">
      <code>new Temporal.Duration(0, 0, 0, 40); -> P40D</code><br />
      <code>new Temporal.Duration(1,0,2); -> P1Y2W</code><br />
      <code>Temporal.Duration.from('P1DT10H')</code><br />
      <code>Temporal.Duration.from('PT1H24M')</code><br />
    </DemoContainer>
    <p>Из объекта Duration можно получить любую секцию даты через свойства</p>
    <DemoContainer title="Свойства">
      <code>
        d = Temporal.Duration.from('P1Y2M3W4DT5H6M7.987654321S');<br>
        d.years -> 1<br>
        d.months -> 2<br>
        d.weeks -> 3<br>
        d.days -> 4<br>
        d.hours -> 5<br>
        d.minutes -> 6<br>
        d.seconds -> 7 <br>
        d.milliseconds -> 987<br>
        d.microseconds -> 654 <br>
        d.nanoseconds -> 321<br>
      </code>
    </DemoContainer>
    <p>Так же доступны методы для модификации</p>
    <DemoContainer title="Методы">
      <pre>// with Можно изменить любую секцию</pre>
      <code>Temporal.Duration.from("PT1H24M").with({'{ years: 1 }'}) -> P1YT1H24M</code>
      <pre>// add Добавить значение</pre>
      <code>Temporal.Duration.from("PT1H24M").add({'{ minutes: 30 }'}) -> PT1H54M</code>
      <pre>// subtract Вычесть значение</pre>
      <code>Temporal.Duration.from("PT1H24M").subtract({'{ minutes: 30 }'}) -> PT54M</code>
      <pre>// abs Получение абсолютного значения</pre>
      <code>Temporal.Duration.from("-PT1H24M").abs() -> PT1H24M</code>
      <pre>// round Округление значения</pre>
      <pre>// Имеет большое количество настроек для округления в большую/меньшею сторону или относительно даты</pre>
      <code>Temporal.Duration.from({'{ minutes: 130 }'}).round({'{ largestUnit: day }'}) -> PT2H10M</code>
      <pre>// Вычисляет количество единиц времени, которые могут поместиться в определенный промежуток времени</pre>
      <pre>// Например можно узнать сколько часов в 1 месяце и 3 днях</pre>
      <code>Temporal.Duration.from("P1M3D").total({'{ unit: "day", relativeTo: "2024-12-11"}'}) -> 34</code>
      <pre>// Представляет человеко-читаемое представление даты относительно языка</pre>
      <pre>// Для этого метода обязательна поддержка Intl.DurationFormat в браузере. Иначе будет выведена строка в формате ISO 8601</pre>
      <code>Temporal.Duration.from('P1DT6H30M').toLocaleString('ru-RU') -> 1 дн. 6 ч 30 мин</code>
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
