<div>
    <Select {...$$restProps} {items} bind:selectedValue />
</div>

<script lang="ts" context="module">
    import Select from 'svelte-select';
</script>

<script lang="ts">
    export let items: [] = [];
    export let selectedValue;
</script>

<style>
    div {
        display: contents;
        --border: 0.05rem solid #bcc3ce;
        --borderRadius: 0.1rem;
        --height: 1.8rem;
        --padding: 5px 8px;
        --inputFontSize: 0.8rem;
        --inputColor: #3b4351;
        --placeholderColor: #bcc3ce;
        --indicatorTop: 8px;
        --clearSelectTop: 8px;
    }
</style>
