<template>
    <div class="tables">
        <!-- первая таблица  -->
        <div class="table-wrap">
            <table cellpadding="0" cellspacing="0" class="table first">
                <tbody>
                    <tr>
                        <th>User name</th>
                        <th>ID</th>
                    </tr>

                    <tr
                        v-for="(tableRow, index) in tableData"
                        :key="tableRow.id"
                        v-on:click="onClick(tableRow.name, index)"
                    >
                        <td class="cell-name">
                            {{ tableRow.name }}
                        </td>

                        <td class="cell-id">{{ tableRow.id }}</td>
                    </tr>
                </tbody>
            </table>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Table',
    props: {
        tableData: {
            type: Array,
            required: true,
        },
        index: Number,
    },
    methods: {
        onClick(name, index) {
            this.$emit('moved-table-row', name, index);
        },
    },
};
</script>
