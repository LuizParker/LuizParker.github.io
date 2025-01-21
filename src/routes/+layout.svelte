<script>
	let { children } = $props();
</script>

<nav>
	<a href="/Inicio">Inicio</a>
	<a href="/Cotação">Dinheiro</a>
	<a href="/Boletim">Nota</a>
	<a href="/Idade">Idade</a>
	<a href="/Temperatura">Temperatura</a>
	<a href="/Atleta">Desempenho</a>
	<a href="/DescCinema">Desconto Cinema</a>
	<a href="/CalcTemp">Calculo da Temperatura</a>
	<a href="/06b-lista-tarefas">CAP 6</a>
	<a href="/Coelhos">Coelhos Fibonacci</a>
	<a href="/Loja">Lojinha</a>
	<a href="/09">filmes</a>
	<a href="/Compras">carrinho</a>
	
</nav>

{@render children()}	