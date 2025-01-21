<script>
    let anoNascimento = $state(2000);  // Definindo o ano de nascimento inicial
    let idade = $state(0);
    let podeVotar = $state(false);

    // Função para calcular a idade e verificar se pode votar
    function calcularIdade() {
        const anoAtual = new Date().getFullYear();  // Pega o ano atual
        idade = anoAtual - anoNascimento;           // Calcula a idade
        podeVotar = idade >= 16;                   // Verifica se tem 16 anos ou mais para votar
    }
</script>

<h1>Verificação de Idade e Voto</h1>

<label for="anoNascimento">Ano de Nascimento:</label>
<input type="number" bind:value={anoNascimento} min="1900" max="2024" />
<br>
<button onclick="{calcularIdade}">Calcular Idade e Verificar Direito ao Voto</button>
<p>Sua idade é: {idade} anos.</p>

{#if podeVotar}
    <p>Você pode votar! 🗳️</p>
{:else}
    <p>Você não pode votar ainda. 😞</p>
{/if}
