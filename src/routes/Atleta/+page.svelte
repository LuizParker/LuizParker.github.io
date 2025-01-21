<script>
    let corrida = 0;
    let flexoes = 0;
    let abdominais = 0;
    let mediaPonderada = 0;
    let conceitoFisico = "";
  
  
    function calcularDesempenho() {
      let pesoCorrida = 4;
      let pesoFlexoes = 3;
      let pesoAbdominais = 3;
     
      mediaPonderada = (corrida * pesoCorrida + flexoes * pesoFlexoes + abdominais * pesoAbdominais) / (pesoCorrida + pesoFlexoes + pesoAbdominais);
     
      if (mediaPonderada >= 8) {
        conceitoFisico = "🏆 Super Atleta! Continue brilhando e inspire outros!";
      } else if (mediaPonderada >= 6) {
        conceitoFisico = "🏋 Determinação Pura! - Você está cada vez mais forte, continue com esse foco!";
      } else if (mediaPonderada >= 4) {
        conceitoFisico = "💪 Em Movimento! - Já está pegando o jeito, bora pegar firme!";
      } else if (mediaPonderada >= 2) {
        conceitoFisico = "🚶 Ainda Sedentário! Está começando a caminhada. Mantenha o ritmo!";
      } else {
        conceitoFisico = "🛋️ Saia do Sofá! - O primeiro passo é levantar e se mexer!";
      }
    }
  </script>
  
  
  <h1> Desempenho Física do Estudante </h1>
  
  
  <label for="corrida">Nota da Corrida de 100 metros (0 a 10): </label>
  <input type="number" id="corrida" bind:value={corrida} min="0" max="10" step="0.1">
  <br>
  
  
  <label for="flexoes">Nota das Flexões (0 a 10): </label>
  <input type="number" id="flexoes" bind:value={flexoes} min="0" max="10" step="0.1">
  <br>
  
  
  <label for="abdominais">Nota dos Abdominais (0 a 10): </label>
  <input type="number" id="abdominais" bind:value={abdominais} min="0" max="10" step="0.1">
  <br>
  
  
  <button on:click={calcularDesempenho}>Calcular Média Ponderada</button>
  
  
  <p>Média Ponderada: {mediaPonderada.toFixed(2)}</p>
  <p>Conceito Físico: {conceitoFisico}</p>
  