<script>
    let title = "Transformações em Dragon Ball";
    let transformations = [
      { name: "Super Saiyajin", description: "Uma das transformações mais icônicas da série, com Goku atingindo esse estado pela primeira vez em Namekusei." },
      { name: "Super Saiyajin Deus", description: "Uma transformação que permite ao usuário acessar o poder dos deuses." },
      { name: "Super Saiyajin Blue", description: "Uma forma que combina o poder do Super Saiyajin com o ki dos deuses." },
      { name: "Ultra Instinct", description: "Uma técnica que separa a mente do corpo, permitindo que o usuário reaja instintivamente aos ataques." }
    ];
  </script>
  
  <main class="transformations-container">
    <h1>{title}</h1>
    <ul>
      {#each transformations as transformation}
        <li>
          <strong>{transformation.name}</strong>: {transformation.description}
        </li>
      {/each}
    </ul>
    <a href="/">Voltar para a página inicial</a>
  </main>
  
  <style>
    .transformations-container {
      max-width: 800px;
      margin: 20px auto; /* Alinha horizontalmente apenas */
      padding: 20px;
      background-color: #fff;
      border-radius: 12px;
      box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    }
  
    h1 {
      color: #9b59b6;
      font-size: 2.5rem;
      margin-bottom: 20px;
    }
  
    ul {
      list-style-type: none;
      padding: 0;
      margin-bottom: 20px;
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
  