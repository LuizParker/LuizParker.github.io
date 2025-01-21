<script>
    let celsius = 0,
    lunitemp = 0;
 
    function c2f() {
        lunitemp = (celsius - 10) / 2.5
    }
 
    function f2c() {
        celsius = lunitemp * 2.5 + 10;
    }
</script>
 
Celsius: <input oninput={c2f} type="number" bind:value={celsius} />
lunitemp: <input oninput={f2c} type="number" bind:value={lunitemp} />
