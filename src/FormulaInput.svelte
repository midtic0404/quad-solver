<script>
    import { createEventDispatcher } from 'svelte';
    let a = 0;
    let b = 0;
    let c = 0;

    const dispatch = createEventDispatcher();

    function hasInputA(event) {
        a = +event.target.value;
        dispatch('inputA', {id: 'a', value: a});
    }

    function hasInputB(event) {
        b = +event.target.value;
        dispatch('inputB', {id: 'b', value: b});
    }

    function hasInputC(event) {
        c = +event.target.value;
        dispatch('inputC', {id: 'c', value: c});
    }

</script>

<style>

</style>

<div class="columns">
    <div class="column">
        <div class="field">
            <label class="label">For X^2</label>
            <div class="control">
                <input class="input" type="text" placeholder="Text input" on:input="{hasInputA}">
            </div>
        </div>
    </div>
    <div class="column">
        <div class="field">
            <label class="label">For X</label>
            <div class="control">
                <input class="input" type="text" placeholder="Text input" on:input="{hasInputB}">
            </div>
        </div>
    </div>
    <div class="column">
        <div class="field">
            <label class="label">For Constant</label>
            <div class="control">
                <input class="input" type="text" placeholder="Text input" on:input="{hasInputC}">
            </div>
        </div>
    </div>
</div>