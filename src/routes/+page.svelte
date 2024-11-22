<div class="nav-container">
  <a class="nav-link" href="/now">
    <span class="nav-link-title">Now</span>
    <span class="nav-link-desc">Сравнительная таблица с объектом Temporal.Now</span>
  </a>
  <a class="nav-link" href="/chapters/year-month">
    <span class="nav-link-title">PlainYearMonth</span>
    <span class="nav-link-desc">Глава про объект Temporal.PlainYearMonth</span>
  </a>
  <a class="nav-link" href="/chapters/month-day">
    <span class="nav-link-title">PlainMonthDay</span>
    <span class="nav-link-desc">Глава про объект Temporal.PlainMonthDay</span>
  </a>
  <a class="nav-link" href="/chapters/plain-date">
    <span class="nav-link-title">PlainDate</span>
    <span class="nav-link-desc">Глава про объект Temporal.PlainDate</span>
  </a>
  <a class="nav-link" href="/chapters/zoned-date-time">
    <span class="nav-link-title">ZonedDateTime</span>
    <span class="nav-link-desc">Глава про объект Temporal.ZonedDateTime</span>
  </a>
</div>

<style>
  .nav-container {
    display: grid;
    grid-template-columns: 1fr 1fr;
    column-gap: 32px;
    row-gap: 28px;
    width: 960px;
    margin: 0 auto;
  }

  .nav-link {
    display: flex;
    flex-direction: column;
    row-gap: 8px;
    border: 1px solid #2e2e32;
    border-radius: 8px;
    padding: 11px 16px 13px;
    transition: border-color 0.25s;
  }

  .nav-link:hover {
    border: 1px solid #9499ff;
  }

  .nav-link-title {
    color: #9499ff;
    font-size: 1.3em;
    font-weight: 700;
  }

  @media (prefers-color-scheme: light) {
    .nav-link-title {
      color: var(--accent);
    }
  }
</style>
