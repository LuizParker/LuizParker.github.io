<script>
    let title = "Wiki Dragon Ball";
  </script>
  
  <main class="home-container">
    <h1>{title}</h1>
    <p>Bem-vindo ao universo de Dragon Ball! Explore as histórias, conheça os personagens e mergulhe nas transformações épicas!</p>
    <nav>
      <ul>
        <li><a href="/about">História</a></li>
        <li><a href="/characters">Personagens</a></li>
        <li><a href="/transformations">Transformações</a></li>
      </ul>
    </nav>
  </main>
  
  <style>
    .home-container {
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      height: 100vh;
      background-color: #f39c12;
      color: white;
      text-align: center;
    }
  
    h1 {
      font-size: 3rem;
      margin-bottom: 20px;
    }
  
    p {
      font-size: 1.25rem;
      margin-bottom: 30px;
    }
  
    nav ul {
      list-style-type: none;
      padding: 0;
      display: flex;
      justify-content: center;
      gap: 15px;
    }
  
    nav ul li a {
      color: #fff;
      background-color: #3498db;
      padding: 10px 15px;
      border-radius: 8px;
      text-decoration: none;
      transition: background-color 0.3s ease;
    }
  
    nav ul li a:hover {
      background-color: #2ecc71;
    }
  </style>
  