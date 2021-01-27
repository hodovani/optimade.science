<div bind:clientWidth={width}>
    {#await $providers}
        <Loader.Avatars
            backgroundColor="#f3f3f3"
            foregroundColor="#ecebeb"
            count={cols}
            {radius}
            {height}
            {width}
        />
    {:then items}
        <Grid {items} {cols} style="justify-content: center;" let:item>
            <Popover pos="bottom">
                <label slot="trigger">
                    <input
                        name="providers"
                        value={$query.providers.includes(item.id)}
                        disabled={!item.attributes.base_url}
                        type="checkbox"
                        on:click={() => onClick(item.id, $query)}
                    />
                    <Avatar
                        status={$query.providers.includes(item.id)
                            ? 'online'
                            : 'offline'}
                        name={item.attributes.name}
                        len={3}
                        {size}
                    />
                </label>
                <Card>
                    <span slot="title" class="h6">{item.attributes.name}</span>
                    <span slot="subtitle" class="text-small text-gray">
                        {item.attributes.homepage || ''}
                    </span>
                    <span class="text-small">{item.attributes.description}</span
                    >
                </Card>
            </Popover>
        </Grid>
    {/await}
</div>

<script lang="ts" context="module">
    import { query } from 'svelte-pathfinder';

    import Grid from '@/layouts/Grid.svelte';
    import Popover from '@/layouts/Popover.svelte';
    import Card from '@/layouts/Card.svelte';

    import Avatar from '@/components/Avatar';
    import * as Loader from '@/components/loaders';

    import providers from '@/stores/providers';

    import type { Size } from '@/types/size';
    import type { Cols } from '@/layouts/Grid.svelte';

    import { SIZE } from '@/types/const';

    import { lsProviderKey } from '@/config';

    const cols: Cols = 12;
    const size: Size = 'lg';
    const height: number = SIZE[size];
    const radius: number = height / 2;

    let augmentation_mode = false;

    // const ids = localStorage[lsProviderKey]
    //     ? JSON.parse(localStorage.getItem(lsProviderKey))
    //     : providers.map((p) => p.id);

    function onClick(id, q) {
        q.providers = ['id'];
        console.log(q);
        // query.set('');
        // providers.set(['id']);
        // providers.set(($providers) => {
        //     console.log($providers);
        //     $providers = [id];
        //     return $providers;
        // });
        // query.set((value) => {
        //     debugger;
        //     console.log(value);
        //     return value;
        // });
        console.log('onClick');
        // query.set(($query) => {
        //     console.log($query);
        //     return $query;
        // });

        // query.update(($query) => {
        //     console.log('asdasdasd');
        //     if (typeof $query.providers === 'string') {
        //         $query.providers = [$query.providers];
        //     }

        //     // console.log($query.providers.filter(id => ids.includes(id)))
        //     $query.providers =
        //         $query.providers && $query.providers.length
        //             ? $query.providers.filter((id) => ids.includes(id))
        //             : '';
        //     console.log($query.providers);
        //     return $query;
        // });
        // console.log(query.providers);
        // console.log(providers);
        // console.log($query.providers.includes(item.id));
        if (augmentation_mode) {
            // if (state == 'active' || state == 'exclusive') {
            //     var all = document.getElementsByTagName('div');
            //     for (var i = 0; i < all.length; i++) {
            //         all[i].removeAttribute('class');
            //         all[i].classList.add('active');
            //     }
            //     window.augmentation_mode = false;
            // } else {
            //     event.target.classList.add('exclusive');
            // }
        } else {
            // if (state == 'active') {
            //     event.target.classList.remove('active');
            // } else if (state == 'exclusive') {
            //     var all = document.getElementsByTagName('div');
            //     for (var i = 0; i < all.length; i++) {
            //         all[i].removeAttribute('class');
            //         all[i].classList.add('active');
            //     }
            // } else {
            //     var all = document.getElementsByTagName('div');
            //     for (var i = 0; i < all.length; i++) {
            //         all[i].removeAttribute('class');
            //     }
            //     event.target.classList.add('exclusive');
            //     window.augmentation_mode = true;
            // }
        }
    }
</script>

<script lang="ts">
    let width: number = 0;
</script>

<style>
    input[type='checkbox'] {
        display: none;
    }
    label {
        display: block;
        cursor: pointer;
    }
</style>
