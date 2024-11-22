<script>
    const { children, title } = $props();
</script>

<div>
    <p>{title}</p>
    <div class="demo-container">
        {@render children()}
    </div>
</div>

<style>
    p {
        margin-bottom: 3px;
    }
    .demo-container {
        border-radius: 8px;
        padding: 16px;
        background-color: #161618;
    }
    @media (prefers-color-scheme: light) {
        .demo-container {
            background-color: #f6f6f7;
        }
    }
</style>