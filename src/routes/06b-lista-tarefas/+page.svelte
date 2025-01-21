<script>
  const tarefas = $state([]);
  let tarefa = $state();
  let tarefaEditada = $state(''); 
  let editarIndex = $state(null);

  // Função para marcar uma tarefa como concluída
  const concluirTarefa = (index) => {
    tarefas[index].concluida = !tarefas[index].concluida;
  };
</script>

<h2>Tarefas a fazer</h2>

<!-- Campo para adicionar uma nova tarefa -->
<div class="input-container">
  <input placeholder="Adicione uma nova tarefa..." bind:value={tarefa} class="input-tarefa" />
  <button onclick={() => {
    if (tarefa) {
      tarefas.push({ nome: tarefa, concluida: false }); // Cada tarefa é um objeto com nome e estado de conclusão
      tarefa = ''; 
    }
  }} class="btn-adicionar">Adicionar tarefa</button>
</div>

<!-- Tarefas Pendentes -->
<h3 class="section-title">Tarefas Pendentes</h3>
<ul class="lista-tarefas">
  {#each tarefas.filter(t => !t.concluida) as tarefa, i}
    <li class="item-tarefa">
      {#if editarIndex === i}
        <!-- Campo para editar a tarefa -->
        <input bind:value={tarefaEditada} class="input-editar" />
        <button onclick={() => {
          tarefas[i].nome = tarefaEditada; 
          editarIndex = null; 
          tarefaEditada = ''; 
        }} class="btn-salvar">Salvar</button>
      {:else}
        <span class="tarefa">{tarefa.nome}</span>
        <!-- Botão de editar -->
        <button onclick={() => {
          editarIndex = i; 
          tarefaEditada = tarefa.nome; 
        }} class="btn-editar">✏️</button>
      {/if}
      
      <!-- Botão de concluir tarefa -->
      <button onclick={() => concluirTarefa(i)} class="btn-concluir">
        {tarefa.concluida ? "Reabrir" : "Concluir"}
      </button>

      <!-- Botão de excluir -->
      <a href="#/" onclick={() => tarefas.splice(i, 1)} class="btn-excluir">🗑</a>
    </li>
  {/each}
</ul>

<!-- Tarefas Concluídas -->
<h3 class="section-title">Tarefas Concluídas</h3>
<ul class="lista-tarefas">
  {#each tarefas.filter(t => t.concluida) as tarefa, i}
    <li class="item-tarefa concluida">
      <span class="tarefa concluida">{tarefa.nome}</span>
      <button onclick={() => concluirTarefa(i)} class="btn-concluir">Reabrir</button>
      <a href="#/" onclick={() => tarefas.splice(i, 1)} class="btn-excluir">🗑</a>
    </li>
  {/each}
</ul>

<style>
  /* Fonte e título */
  h2 {
    font-family: 'Roboto', sans-serif;
    color: #2c3e50;
    text-align: center;
    font-size: 2rem;
    margin-bottom: 20px;
  }

  .section-title {
    font-family: 'Roboto', sans-serif;
    color: #34495e;
    margin-top: 30px;
    font-size: 1.5rem;
    margin-bottom: 15px;
  }

  /* Input de tarefa */
  .input-container {
    display: flex;
    justify-content: center;
    align-items: center;
    margin-bottom: 20px;
  }

  .input-tarefa {
    padding: 12px 20px;
    width: 70%;
    font-size: 1rem;
    border-radius: 10px;
    border: 1px solid #ddd;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
    transition: 0.3s;
  }

  .input-tarefa:focus {
    border-color: #3498db;
    outline: none;
  }

  /* Botão de adicionar tarefa */
  .btn-adicionar {
    padding: 12px 20px;
    font-size: 1rem;
    background-color: #3498db;
    color: white;
    border: none;
    border-radius: 10px;
    cursor: pointer;
    transition: 0.3s;
    margin-left: 10px;
  }

  .btn-adicionar:hover {
    background-color: #2980b9;
  }

  /* Lista de tarefas */
  .lista-tarefas {
    list-style-type: none;
    padding: 0;
    width: 70%;
    margin: 0 auto;
  }

  .item-tarefa {
    background-color: #ffffff;
    padding: 15px;
    margin-bottom: 15px;
    border-radius: 10px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
    transition: 0.3s;
  }

  .item-tarefa:hover {
    background-color: #ecf0f1;
  }

  .item-tarefa.concluida {
    background-color: #eaf7e2;
    color: #7f8c8d;
    text-decoration: line-through;
  }

  /* Botões de editar, excluir e concluir */
  .btn-editar, .btn-excluir, .btn-concluir {
    background: none;
    border: none;
    color: #555;
    cursor: pointer;
    font-size: 18px;
    transition: 0.3s;
    padding: 8px 12px;
    border-radius: 6px;
  }

  .btn-editar:hover, .btn-excluir:hover, .btn-concluir:hover {
    color: #2980b9;
  }

  .btn-concluir {
    background-color: #f39c12;
    color: white;
    border-radius: 6px;
  }

  .btn-concluir:hover {
    background-color: #e67e22;
  }

  .btn-excluir {
    color: #e74c3c;
  }

  /* Input de edição */
  .input-editar {
    padding: 5px 12px;
    font-size: 1rem;
    border-radius: 6px;
    border: 1px solid #ddd;
    width: 60%;
    transition: 0.3s;
  }

  .input-editar:focus {
    border-color: #3498db;
    outline: none;
  }

  /* Tarefa em destaque */
  .tarefa {
    flex-grow: 1;
  }
</style>
