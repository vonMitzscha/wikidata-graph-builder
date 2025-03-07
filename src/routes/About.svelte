<script lang="ts">
    const link = (params: Record<string, string>) =>
        "?" + new URLSearchParams(params).toString();

    const examples = {
        "State-organization Duchy Saxe-Gotha-Altenburg (organisation chart)": {
            item: "Q40154",
            property: "P428",
            mode: "reverse",
            graph_direction: "left",
            lang: "de",
        },
        "State-organization Duchy Saxe-Gotha-Altenburg with number of employees": {
            item: "Q40154",
            property: "P428",
            mode: "reverse",
            size_property: "P315",
            lang: "de",
        },
        "Pedigree of Duke Ernst II of Saxe-Gotha-Altenburg": {
            item: "Q978",
            property: "P150",
            mode: "reverse",
            graph_direction: "down",
        },
        "Continuing font grades from Cicero": {
            item: "Q1194171",
            property: "P6",
            mode: "both",
            graph_direction: "down",
            lang: "de",
        },
        "OhdABTaxonomy of Speculoos baker": {
            property: "P1007",
            item: "Q673131",
            graph_direction: "up",
        },
        "Types of baker in OhdAB": {
            property: "P1007",
            item: "Q520368",
            mode: "reverse",
            iterations: "1",
            graph_direction: "right",
        }, 
    };
</script>

<h1 class="text-3xl md:text-4xl my-8">FactGrid Graph Builder</h1>
<p>
    Build graphs using
    <a href="https://database.factgrid.de/wiki/Main_Page">FactGrid </a>
    <a href="https://database.factgrid.de/query/">Query Service</a>.
</p>
<p>Examples:</p>
<ul>
    {#each Object.entries(examples) as [name, params]}
        <li>
            <a href={link(params)}>
                {name}
            </a>
        </li>
    {/each}
</ul>
<p class="text-sm">
    The source code released under
    <a href="https://opensource.org/licenses/MIT">MIT license </a>
    at
    <a href="https://github.com/vonMitzscha/wikidata-graph-builder"> GitHub</a>. 
    The tool was originally developed by
    <a href="https://github.com/AngryLoki/wikidata-graph-builder"> AngryLoki</a>.
</p>

<style lang="postcss">
    a {
        @apply text-blue-600 hover:underline;
    }

    p {
        @apply mb-3 text-gray-800;
    }

    ul {
        @apply ml-4 mb-3 list-disc list-inside;
    }
</style>
