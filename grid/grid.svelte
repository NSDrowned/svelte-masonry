<script>
    import { onMount } from 'svelte';
    import Postbit from '../postbit/postbit.svelte';
    import Masonry from '../svelte-masonry/svelte-masonry.svelte';
    import axios from 'axios';

    let items = [];
    let maxColumns = 10;

    onMount(() => {
        axios.get('https://jsonplaceholder.typicode.com/posts').then((response) => {
            items = response.data;
        });
    });

</script>

<Masonry items={items} component={Postbit} maxcolumns={maxColumns}></Masonry>