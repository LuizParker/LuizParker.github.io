<script>
    let np = $state(0);
    let nt = $state(0);
    let ns = $state(0);
    let nf = $state(0);

    function calcularnota() {
        nf = (np * 5 + ns * 3 + nt * 2) / 10;
    }
    
</script>

<h1>Boletim Escolar</h1>

Nota da prova:<input type="number" bind:value={np}
min="0" max="10" />
<br>
Nota da trabalho:<input type="number" bind:value={nt}
min="0" max="10" />
<br>
Nota do seminário:<input type="number" bind:value={ns}
min="0" max="10" />
<br>
<button onclick="{calcularnota}">Calcule sua nota final</button>
<p>Sua nota finla  é: {nf}</p>

 {#if nf > 8.5}
    <p>Conceito A: Aprovado 😁</p>
 {:else if nf > 7}
    <p>Conceito B: Aprovado 😊</p>
 {:else if nf > 5}
    <p>Conceito C: Aprovado 😊</p>
 {:else if nf > 2.5}
    <p>Conceito D: Recuperação 😓</p>
 {:else}
    <p>Conceito E: Reprovado 😢😭</p>
 {/if}