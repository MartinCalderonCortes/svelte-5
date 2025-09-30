<script lang="ts">
    function onsubmit(event: SubmitEvent) {
        event.preventDefault();
        const data = new FormData(this)
        const email = data.get('emailForm')
        console.log(email)
    }
</script>

<form {onsubmit}>
    <input type="email" name="emailForm"/>
    <button type="submit">Subscribe</button>
</form>