<script>
  const props = $props();
</script>

<section>
  <h3>{props.title}</h3>
  <table>
    <thead>
      <tr>
        <th scope="col">Цель</th>
        <th scope="col">Temporal</th>
        <th scope="col">Date-fns</th>
        <th scope="col">Date</th>
      </tr>
    </thead>
    <tbody>
      {#each props.data as row}
        <tr>
          <td>{row.description}</td>
          <td>
            <div>
              <span>Вызов: </span>
              <code>{row.temporal.call}</code>
            </div>
            <div>
              <span>Результат:</span>
              {row.temporal.output}
            </div>
          </td>
          <td>
            <div>
              <span>Вызов: </span>
              <code>{row.dateFns.call}</code>
            </div>
            <div>
              <span>Результат:</span>
              {row.dateFns.output}
            </div>
          </td>
          <td>
            <div>
              <span>Вызов: </span>
              <code>{row.dateJs.call}</code>
            </div>
            <div>
              <span>Результат:</span>
              {row.dateJs.output}
            </div>
          </td>
        </tr>
      {/each}
    </tbody>
  </table>
</section>

<style>
  table {
    width: 100%;
    border-collapse: collapse;
    border-spacing: 0;
  }
  th,
  td {
    padding: 10px 15px;
    vertical-align: middle;
    border: 1px solid #2e2e32;
  }
  thead {
    background-color: #3b3b48;
    color: rgba(235, 235, 245, 0.6);
  }
  tbody tr:nth-child(even) {
    background: #3b3b48;
  }
</style>
