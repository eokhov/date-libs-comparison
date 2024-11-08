<script>
  const { title, tableBody, tableHead } = $props();
</script>

<section>
  <h3>{title}</h3>
  <table>
    <thead>
      <tr>
        {#each tableHead as column}
          <th scope="col">{column}</th>
        {/each}
      </tr>
    </thead>
    <tbody>
      {#each tableBody as row}
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
          {#if row.dateJs}
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
          {/if}
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
    background: #202127;
  }

  @media (prefers-color-scheme: light) {
    thead {
      background-color: #f6f6f7;
      color: rgba(51, 51, 51, 0.87);
    }
    tbody tr:nth-child(even) {
      background: #f6f6f7;
    }
  }
</style>
