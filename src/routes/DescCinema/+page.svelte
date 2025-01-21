<script>
    let idade = 0;      // Definir a idade inicial
    let desconto = 0;   // Definir o desconto inicial

    // Função para calcular o desconto baseado na idade
    function calcularDesconto() {
        if (idade <= 12) {
            desconto = 50;  // 50% de desconto para crianças até 12 anos
        } else if (idade >= 13 && idade <= 17) {
            desconto = 30;  // 30% de desconto para adolescentes entre 13 e 17 anos
        } else if (idade >= 60) {
            desconto = 40;  // 40% de desconto para idosos com 60 anos ou mais
        } else {
            desconto = 0;   // Sem desconto para outras idades
        }
    }
</script>

<h1>Verificação de Desconto no Cinema</h1>

<label for="idade">Idade:</label>
<input type="number" bind:value={idade} min="0" max="120" on:input={calcularDesconto} />
<br>

<p>Sua idade é: {idade} anos.</p>

<p>O desconto aplicável é: {desconto}%.</p>

{#if desconto > 0}
    <p>Você tem um desconto de {desconto}% no ingresso!</p>
{:else}
    <p>Você não tem desconto.</p>
{/if}
