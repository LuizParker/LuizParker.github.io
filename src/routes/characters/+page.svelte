<script>
    let title = "Personagens de Dragon Ball";
    let characters = [
      { name: "Goku", description: "Protagonista da série e o Saiyajin mais forte do universo." },
      { name: "Vegeta", description: "Príncipe dos Saiyajins e rival de Goku." },
      { name: "Bulma", description: "Gênio da Capsule Corporation e amiga de Goku." },
      { name: "Freeza", description: "Um dos vilões mais icônicos da série." }
    ];
  </script>
  
  <main class="characters-container">
    <h1>{title}</h1>
    <ul>
      {#each characters as character}
        <li>
          <strong>{character.name}</strong>: {character.description}
        </li>
      {/each}
    </ul>
    <a href="/">Voltar para a página inicial</a>
  </main>
  
  <style>
    .characters-container {
      max-width: 800px;
      margin: 30px auto;
      padding: 20px;
      background-color: #fff;
      border-radius: 12px;
      box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    }
  
    h1 {
      color: #2ecc71;
      font-size: 2.5rem;
      margin-bottom: 20px;
    }
  
    ul {
      list-style-type: none;
      padding: 0;
    }
  
    li {
      background-color: #f1f1f1;
      padding: 15px;
      margin-bottom: 10px;
      border-radius: 8px;
      transition: background-color 0.3s ease;
    }
  
    li:hover {
      background-color: #e1e1e1;
    }
  
    a {
      display: inline-block;
      margin-top: 20px;
      padding: 10px 15px;
      background-color: #3498db;
      color: white;
      border-radius: 8px;
      text-decoration: none;
      transition: background-color 0.3s ease;
    }
  
    a:hover {
      background-color: #2ecc71;
    }
  </style>
  