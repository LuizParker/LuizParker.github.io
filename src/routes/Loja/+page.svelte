<script>
    import Produto from '$lib/components/Produto.svelte';
    import { writable } from 'svelte/store';

    // Lista de produtos (filmes)
    let products = [
        {
            img: 'https://cdn.awsli.com.br/2500x2500/1610/1610163/produto/177685212/poster-os-vingadores-ultimato-a-242769bd.jpg',
            title: 'Vingadores: Ultimato',
            description:
                'Os Vingadores se reúnem para a última batalha contra Thanos, na tentativa de reverter os danos causados ao universo.',
            price: 49.99
        },
        {
            img: 'https://www.universalpics.com.br/tl_files/content/movies/jurassic_world_dominion/poster/01.jpg',
            title: 'Jurassic World: Domínio',
            description:
                'Após a destruição do parque, dinossauros começam a se espalhar pelo mundo, causando caos e medo nas cidades.',
            price: 39.99
        },
        {
            img: 'https://a-static.mlcdn.com.br/1500x1500/poster-cartaz-matrix-4-resurrections-a-pop-arte-poster/poparteskins2/15938542620/9946bc26fa01d2801673088ce8e63e52.jpeg',
            title: 'Matrix Resurrections',
            description:
                'Neo retorna ao mundo virtual para descobrir novos segredos sobre a Matrix e sua própria existência.',
            price: 59.99
        },
        {
            img: 'https://upload.wikimedia.org/wikipedia/pt/2/2b/Spider-Man_No_Way_Home_-_The_More_Fun_Stuff_Version_poster.jpg',
            title: 'Spider-Man: No Way Home',
            description:
                'Peter Parker lida com as consequências de sua identidade secreta ser revelada ao mundo, buscando ajuda em diferentes dimensões.',
            price: 69.99
        }
    ];

    // Estado do carrinho
    const cart = writable([]);

    // Estado da mensagem de compra
    let purchaseMessage = writable('');

    // Função para adicionar produtos ao carrinho
    function addToCart(product) {
        cart.update((currentCart) => [...currentCart, product]);
    }

    // Função para finalizar a compra
    function finalizePurchase() {
        cart.set([]); // Limpa o carrinho
        purchaseMessage.set('Compra realizada com sucesso!'); // Mostra mensagem de sucesso

        // Remove a mensagem após 3 segundos
        setTimeout(() => {
            purchaseMessage.set('');
        }, 3000);
    }
</script>

<div class="container mt-5">
    <h1>Loja de Filmes</h1>

    <!-- Exibição dos produtos -->
    <div class="row">
        {#each products as product}
            <div class="col-md-3 mb-4">
                <Produto 
                    img={product.img}
                    title={product.title}
                    description={product.description}
                    price={product.price}
                    addToCart={addToCart}
                />
            </div>
        {/each}
    </div>

    <!-- Exibição do carrinho de compras -->
    <div class="mt-5">
        <h3>Carrinho de Compras</h3>

        {#if $cart.length > 0}
            <ul>
                {#each $cart as item}
                    <li>{item.title} - R$ {item.price.toFixed(2)}</li>
                {/each}
            </ul>
            <p>
                <strong>Total: R$ {$cart.reduce((total, item) => total + item.price, 0).toFixed(2)}</strong>
            </p>
            <button class="btn btn-danger" on:click={finalizePurchase}>Finalizar Compra</button>
        {:else}
            <p>Seu carrinho está vazio.</p>
        {/if}

        <!-- Mensagem de sucesso após a compra -->
        {#if $purchaseMessage}
            <div class="alert alert-success mt-3">{$purchaseMessage}</div>
        {/if}
    </div>
</div>

<style>
    .container {
        margin-top: 30px;
    }
    .btn-danger {
        background-color: #dc3545;
        border: none;
    }
    .btn-danger:hover {
        background-color: #c82333;
    }
    .alert-success {
        color: #155724;
        background-color: #d4edda;
        border-color: #c3e6cb;
        padding: 10px;
        border-radius: 5px;
    }
</style>