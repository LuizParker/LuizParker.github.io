<script>
    let carros = [
        { nome: "Sedan", preco: 25000 },
        { nome: "SUV", preco: 45000 },
        { nome: "Hatch", preco: 20000 },
        { nome: "Picape", preco: 30000 },
        { nome: "Conversível", preco: 35000 }
    ];

    let carrosSelecionados = [];
    let textoFiltro = '';

    function filtrarCarros() {
        return carros.filter(carro => carro.nome.toLowerCase().includes(textoFiltro.toLowerCase()));
    }

    function selecionarCarro(event, carro) {
        if (event.target.checked) {
            carrosSelecionados.push(carro);
        } else {
            carrosSelecionados = carrosSelecionados.filter(item => item !== carro);
        }
        atualizarResumo();
    }

    function selecionarTodos() {
        carrosSelecionados = [...carros];
        atualizarResumo();
    }

    function limparSelecao() {
        carrosSelecionados = [];
        atualizarResumo();
    }

    function atualizarResumo() {
        document.getElementById('itemCount').innerText = carrosSelecionados.length;
        document.getElementById('totalPrice').innerText = totalSelecionado().toFixed(2);
    }

    function finalizarCompra() {
        alert(`Resumo da compra:\n${carrosSelecionados.map(carro => carro.nome).join(", ")}\nTotal: R$ ${totalSelecionado().toFixed(2)}`);
    }

    function totalSelecionado() {
        return carrosSelecionados.reduce((total, carro) => total + carro.preco, 0);
    }
</script>

<h1>Carrinho de Compras - Carros</h1>

<input 
    class="form-control mb-3" 
    placeholder="Filtrar por nome..." 
    on:input={(event) => textoFiltro = event.target.value}
/>

<div class="row">
    {#each filtrarCarros() as carro}
        <div class="col-md-6">
            <div class="form-check">
                <input 
                    class="form-check-input" 
                    type="checkbox" 
                    id={carro.nome}
                    on:change={(event) => selecionarCarro(event, carro)} 
                    checked={carrosSelecionados.includes(carro)}
                />
                <label class="form-check-label" for={carro.nome}>
                    {carro.nome} - R$ {carro.preco.toFixed(2)}
                </label>
            </div>
        </div>
    {/each}
</div>

<div class="mt-4">
    <button on:click={selecionarTodos} class="btn btn-primary me-2">Selecionar Tudo</button>
    <button on:click={limparSelecao} class="btn btn-secondary me-2">Limpar Seleção</button>
</div>

<div class="summary mt-3">
    <p>Total de itens selecionados: <span id="itemCount">0</span></p>
    <p>Valor total: R$ <span id="totalPrice">0.00</span></p>
</div>

<button on:click={finalizarCompra} class="btn btn-success mt-2">Finalizar Compra</button>
