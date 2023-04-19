<script lang="ts">
    import { Container, Display, Sprite, Panel } from '~/components';
    import type { PageData } from './$houdini';
	import type { Info$input, Info$result, InfoStore, QueryStore } from '$houdini'

    export let data: PageData

    $: ({ Info } = data)

    let infoStore: InfoStore = Info;
    // I get this error at Info$input:
    // Type 'null' does not satisfy the constraint '{}'.
    let queryStore: QueryStore<Info$result, Info$input> = infoStore;

    $: species = $Info.data?.species;
</script>

{#if species}
    <Container>
        <Panel slot="left">
            <Display id="species-name">
                {species.name}
                <span>no.{species.id}</span>
            </Display>
            <Sprite
                id="species-sprite"
                src={species.sprites.front}
                speciesName={species.name}
            />
            <Display id="species-flavor_text">
                {species.flavor_text}
            </Display>
        </Panel>
    </Container>
{/if}
