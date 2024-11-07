<script>
    import { Temporal } from "temporal-polyfill";

    const currentTimeZone = Temporal.Now.timeZoneId();
    const currentDateTimeString = Temporal.Now.instant().toZonedDateTimeISO(currentTimeZone).toInstant();
    console.log(currentDateTimeString);
    
    console.log(Temporal.Instant.from(currentDateTimeString).toString());
    
</script>

<main>
    Instant page
</main>