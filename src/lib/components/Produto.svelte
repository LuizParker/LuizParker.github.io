<script>
    export let img;
    export let title;
    export let description;
    export let price;
    export let addToCart;
</script>

<div class="card h-100" style="width: 18rem;">
    <img src={img} class="card-img-top" alt={title} width="200px" />
    <div class="card-body">
        <h5 class="card-title">{title}</h5>
        <p class="card-text">{description}</p>
        <p class="card-text">Preço: R$ {price.toFixed(2)}</p>
        <button class="btn btn-primary" on:click={() => addToCart({ img, title, description, price })}>
            Adicionar ao Carrinho
        </button>
    </div>
</div>

<style>
    .card {
        border: 1px solid #ddd;
        margin-bottom: 20px;
    }
    button {
        width: 100%;
    }
    .btn-primary {
        background-color: #007bff;
        border: none;
    }
    .btn-primary:hover {
        background-color: #0056b3;
    }
</style>
