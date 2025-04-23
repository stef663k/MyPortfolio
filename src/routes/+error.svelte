<script>
    import { page } from "$app/state";
</script>
<title>{page.status}</title>
<div class="error">
    <div class="error-content">
        <h1>{page.status}</h1>
        <p>{page.error?.message ?? "Not Found"}</p>
    </div>
</div>

<style>
    .error {
        display: flex;
        justify-content: center;
        align-items: center;
        min-height: calc(100vh - 75px);
    }

    .error-content {
        text-align: center;
        background: rgba(255, 255, 255, 0.8);
        border-radius: 0.8rem;
        padding: 2rem 4rem;
        box-shadow: 0 8px 32px rgba(0,0,0,0.1);
        border: 1px solid rgba(255, 255, 255, 0.3);
    }

    h1 {
        font-size: 3rem;
        margin: 0;
        color: #dc3545;
    }

    p {
        font-size: 1.25rem;
        color: #636e72;
        margin: 0;
    }
</style>