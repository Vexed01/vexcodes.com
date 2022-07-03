<section class="jsonify">
    <form>
        <label for="fname">First name:</label><br>
        <input type="text" id="fname" name="fname"><br>
        <label for="lname">Last name:</label><br>
        <input type="text" id="lname" name="lname"><br>

        <button type="submit">Submit</button>
    </form>
</section>

<div class="results">
    <h2>Form Data</h2>
    <pre></pre>
</div>

<script>
    function handleSubmit(event) {
        event.preventDefault();

        const data = new FormData(event.target);

        const formJSON = Object.fromEntries(data.entries());

        // // for multi-selects, we need special handling
        // formJSON.snacks = data.getAll('snacks');

        const results = document.querySelector('.results pre');
        results.innerText = JSON.stringify(formJSON, null, 2);
    }

    const form = document.querySelector('.jsonify');
    form.addEventListener('submit', handleSubmit);
</script>
