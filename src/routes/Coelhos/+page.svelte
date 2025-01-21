<script>
    import { writable } from 'svelte/store';

    // Estado para armazenar os números de Fibonacci e o mês atual
    let fibonacciNumbers = writable([0, 1]);
    let currentMonth = writable(0);

    // Função para calcular o próximo número de Fibonacci
    function increaseFibonacciNumbers() {
        fibonacciNumbers.update(fib => {
            let last = fib[fib.length - 1];
            let secondlast = fib[fib.length - 2];
            return [...fib, last + secondlast];
        });

        currentMonth.update(month => month + 1);
    }

    // Função para voltar para o mês anterior
    function decreaseFibonacciNumbers() {
        fibonacciNumbers.update(fib => fib.slice(0, fib.length - 1));
        currentMonth.update(month => month > 0 ? month - 1 : 0);
    }

    // Função para mudar o mês manualmente
    function changeMonth(event) {
        let newMonth = parseInt(event.target.value);
        if (newMonth >= 0 && newMonth < fibonacciNumbers.length) {
            currentMonth.set(newMonth);
        }
    }
</script>

<h1>Os coelhos de Fibonacci</h1>

<!-- Controle de mês -->
<p>
    Mês: 
    <input 
        type="number" 
        min="0" 
        bind:value={$currentMonth} 
        on:input={changeMonth} 
        max={fibonacciNumbers.length - 1} 
    />
    <button on:click={increaseFibonacciNumbers}>Próximo mês</button>
    <button on:click={decreaseFibonacciNumbers}>Mês anterior</button>
</p>

<!-- Mensagem sobre os coelhos -->
<p>Após {$currentMonth} meses, haverá {$fibonacciNumbers[$currentMonth]} ninhadas de coelhos, totalizando {$fibonacciNumbers[$currentMonth] * 2} coelhos!</p>

<style>
    h1 {
        color: #333;
    }
    button {
        margin-left: 10px;
        padding: 5px 10px;
        background-color: #007bff;
        color: white;
        border: none;
        border-radius: 5px;
        cursor: pointer;
    }
    button:hover {
        background-color: #0056b3;
    }
    input {
        width: 60px;
        padding: 5px;
        margin-right: 10px;
    }
</style>
