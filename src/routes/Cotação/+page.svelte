<script>
    let D = 0; // Valor do Dólar
    let R = 0; // Valor do Real
    let DR = 0; // Dólar para Real
    let RD = 0; // Real para Dólar

    // Função para calcular Dólar para Real
    function converterDolarParaReal() {
        DR = D * 5.76;
    }

    // Função para calcular Real para Dólar
    function converterRealParaDolar() {
        RD = R / 5.76;
    }

    // Reatividade para atualizar as variáveis conforme os inputs
    $: {
        if (D !== 0) {
            converterDolarParaReal(); // Atualiza o valor de DR quando D mudar
        }
        if (R !== 0) {
            converterRealParaDolar(); // Atualiza o valor de RD quando R mudar
        }
    }
</script>

<h1>Cotação do Dolar</h1>

<!-- Input de Dólar -->
Valor do Dólar: <input type="number" bind:value={D} />
<br>

<!-- Input de Real -->
Valor do Real: <input type="number" bind:value={R} />
<br>

<!-- Exibição de Dólar para Real -->
Dólar para Real: <input type="number" bind:value={DR} readonly />
<br>

<!-- Exibição de Real para Dólar -->
Real para Dólar: <input type="number" bind:value={RD} readonly />
