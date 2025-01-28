<script>
    let title = "História de Dragon Ball";
    let content = `Dragon Ball é uma franquia de mídia japonesa criada por Akira Toriyama. 
    A história segue as aventuras de Son Goku desde a sua infância até a vida adulta, enquanto ele treina artes marciais e explora o mundo em busca das Esferas do Dragão, que concedem desejos. 
    A série é dividida em diferentes sagas como Dragon Ball, Dragon Ball Z, Dragon Ball Super, entre outras.`;
  </script>
  
  <main class="about-container">
    <h1>{title}</h1>
    <p>{content}</p>
    <a href="/">Voltar para a página inicial</a>
  </main>
  
  <style>
    .about-container {
      max-width: 800px;
      margin: 30px auto;
      padding: 20px;
      background-color: #fff;
      border-radius: 12px;
      box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    }
  
    h1 {
      color: #e74c3c;
      font-size: 2.5rem;
      margin-bottom: 20px;
    }
  
    p {
      font-size: 1.125rem;
      line-height: 1.8;
      margin-bottom: 20px;
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
  