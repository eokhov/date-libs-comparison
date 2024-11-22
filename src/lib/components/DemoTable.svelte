<script>
  import DemoContainer from "./DemoContainer.svelte";
  const props = $props();
</script>

<DemoContainer>
  <table>
    <thead>
      <tr>
        <th scope="col" class="item-call">Вызов</th>
        <th scope="col" class="item-output">Результат</th>
        <th scope="col" class="item-description">Цель</th>
      </tr>
    </thead>
    <tbody>
      {#each props.data as row}
        <tr>
          <td class="item-call"><pre>{row.call}</pre></td>
          <td class="item-output">{row.output}</td>
          <td class="item-description">{row.description}</td>
        </tr>
      {/each}
    </tbody>
  </table>
</DemoContainer>

<style>
  table {
    width: 100%;
    border-collapse: collapse;
    border-spacing: 0;
  }
  thead {
    color: rgba(235, 235, 245, 0.6);
  }
  th,
  td {
    padding-inline: 15px;
    vertical-align: middle;
  }

  th {
    padding-block: 15px;
  }
  td {
    padding-block: 10px;
  }

  .item-call {
    text-align: left;
  }
  .item-output {
    text-align: center;
  }
  .item-description {
    text-align: right;
  }
  @media (prefers-color-scheme: light) {
    thead {
      color: rgba(60, 60, 67, 0.78);
    }
  }
</style>
