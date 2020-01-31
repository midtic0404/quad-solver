<script>
    export let data = {
        a:0,
        b:0,
        c:0
    };

    let description;
    let solutions = [];
    let smallEquationResult;

    $: a = data['a'];
    $: b = data['b'];
    $: c = data['c'];

    $: if(a === 0 && b === 0 && c !== 0) {
        solutions = [];
        description = "No solutions";
    }else if(a === 0) {
        solutions = [];
        description = "There are infinite solutions";
    }else {
        solutions = [];
        smallEquationResult = (b * b) - (4 * a * c);
        if (smallEquationResult < 0) {
            description = "No real solutions";
        }else if (smallEquationResult > 0) {
            description = "There are two solutions";
            solutions.push((-b + Math.sqrt(smallEquationResult))/(2*a));
            solutions.push((-b - Math.sqrt(smallEquationResult))/(2*a));
        }else {
            description = "There is one solution";
            solutions.push((-b + Math.sqrt(smallEquationResult))/(2*a));
        }
    }

    
</script>

<style>
    section {
        display: flex;
        justify-content: center;
        align-items: center;
    }

    h1 {
        font-size:  6rem;
    }

    .container {
        text-align: center;
    }
</style>

<section class="hero is-light is-medium">
  <div class="hero-body">
    <div class="container">
      <h1 class="title">
        {`${a}x^2 + ${b}x + ${c} = 0`}
      </h1>
      <h2 class="subtitle">{description}</h2>
      {#if solutions}
        <div class="columns">
           {#each solutions as solution, i (i) }
                <div class="column">
                    <div class="card">
                        <div class="card-content">
                            <h1 class="title is-size-1">x = {solution.toFixed(1)}</h1>
                        </div>
                    </div>
                </div>
           {/each}
        </div>
      {/if}
    </div>
  </div>
</section>