<!--
Copyright: Ankitects Pty Ltd and contributors
License: GNU AGPL, version 3 or later; http://www.gnu.org/licenses/agpl.html
-->
<script lang="ts">
    import { type ImportCsvState } from "./lib";

    export let state: ImportCsvState;

    const metadata = state.metadata;
    const columnOptions = state.columnOptions;
</script>

<div class="outer">
    <table class="preview">
        <thead>
            <tr>
                {#each $columnOptions.slice(1) as { label, shortLabel }}
                    <th>
                        {shortLabel || label}
                    </th>
                {/each}
            </tr>
        </thead>
        <tbody>
            {#each $metadata.preview as row}
                <tr>
                    {#each row.vals as cell}
                        <td>{cell}</td>
                    {/each}
                </tr>
            {/each}
        </tbody>
    </table>
</div>

<style lang="scss">
    .outer {
        overflow: auto;
    }

    .preview {
        border-collapse: collapse;
        white-space: nowrap;

        th,
        td {
            text-overflow: ellipsis;
            overflow: hidden;
            border: 1px solid var(--border-subtle);
            padding: 0.25rem 0.5rem;
            max-width: 15em;
        }

        th {
            background: var(--border);
            text-align: center;
        }

        tr {
            &:nth-child(even) {
                background: var(--canvas);
            }
        }

        td {
            text-align: start;
        }
    }
</style>
