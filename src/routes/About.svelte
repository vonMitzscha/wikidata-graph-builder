<script lang="ts">
    const link = (params: Record<string, string>) =>
        "?" + new URLSearchParams(params).toString();

    const examples = {
        "State-organization Duchy Saxe-Gotha-Altenburg (force-based)": {
            item: "Q40154",
            property: "P8",
            mode: "reverse",
        },
        "Class tree for human (directed)": {
            item: "Q5",
            property: "P279",
            graph_direction: "down",
        },
        "Parents of Nikita Mikhalkov (directed)": {
            item: "Q55207",
            property: "P40",
            mode: "reverse",
            iterations: "20",
            graph_direction: "down",
        },
        "Children of Agnes of the Palatinate (force-based, 4 generations)": {
            property: "P40",
            item: "Q4450926",
            iterations: "4",
        },
        "Types of integers (force-based, counting instances of each type)": {
            property: "P279",
            item: "Q12503",
            mode: "reverse",
            size_property: "P31",
        },
        "Subclasses of physicists (force-based, counting people by occupation)":
            {
                property: "P279",
                item: "Q169470",
                mode: "reverse",
                size_property: "P106",
            },
        "Subclasses and parent classes of nonmetals (force-based)": {
            property: "P279",
            item: "Q19600",
            mode: "both",
        },
        "People, who were filmed with Jim Carrey": {
            property: "P161",
            item: "Q40504",
            mode: "undirected",
            iterations: "2",
        },
        "All-directional family tree of William Shakespeare": {
            property: "P40",
            item: "Q692",
            mode: "undirected",
            iterations: "4",
            graph_direction: "down",
        },
        "Is Jesus a descendant of Adam of the 53rd tribe?": {
            property: "P40",
            item: "Q70899",
            iterations: "60",
            graph_direction: "down",
        },
        "Force-directed graph drawing is surely an entity": {
            property: "P279",
            item: "Q3076841",
            graph_direction: "down",
        },
        "Connectivity of the USA states (custom query)": {
            mode: "wdqs",
            wdqs: `\
SELECT ?item ?itemLabel ?linkTo {
?item wdt:P31 wd:Q35657 .
OPTIONAL { ?linkTo wdt:P47 ?item ; wdt:P31 wd:Q35657 } .

SERVICE wikibase:label {bd:serviceParam wikibase:language "en" }
}`,
        },
        "Usage of subclasses of actors": {
            property: "P279",
            item: "Q33999",
            mode: "reverse",
            size_property: "P106",
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
    <a href="https://github.com/vonMitzscha/wikidata-graph-builder"> GitHub </a>.
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
