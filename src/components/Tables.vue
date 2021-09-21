<template>
  <div class="tables">

    <!-- первая таблица  -->
    <div class="table-wrap">
      <table cellpadding="0" cellspacing="0" class="table first">
        <tbody>
          <tr>
            <th> User name</th>
            <th>ID</th>
          </tr>
          <tr
              v-for="(firstTableRow, index2) in firstTableData"
              :key="firstTableRow.id"
              v-on:click="$emit('moved-first-table-row', firstTableRow.name, index2)"
          >
            <td class="cell-name">
              {{firstTableRow.name}}</td>
            <td class="cell-id">{{firstTableRow.id}}</td>
          </tr> 
        </tbody>
      </table>
    </div>

    <!-- вторая таблица  -->
    <div class="table-wrap">
      <table cellpadding="0" cellspacing="0" class="table second">
        <tbody>
          <tr>
            <th>User name</th>
            <th>ID</th>
          </tr>
          <tr
              v-for="(secondTableRow, index) in secondTableData"
              :key="secondTableRow.id"
              v-on:click="$emit('moved-second-table-row', secondTableRow.name, index)"
          >
            <td class="cell-name">
              {{ secondTableRow.name }}
            </td>
            <td class="cell-id">{{ secondTableRow.id }}</td>
          </tr>

        </tbody>
      </table>
    </div>
  </div>
</template>

<script>


export default {
  name: 'Tables',
  // props: ["secondTableData"],
  props: {
    secondTableData: {
      type: Array,
      required: true,
    },
    firstTableData: {
      type: Array,
      required: true,
    },
    index: Number,
    index2: Number
  },
    data() {
      // return {
      //   firstTableData: firstTableUsers
      // };
    },
    methods: {
      movedSecondTableRow(name, id, index) {
        this.$emit('moved-second-table-row', name, id, index)
      },
      movedFirstTableRow(name, id, index2) {
        this.$emit('moved-first-table-row', name, id, index2)
      }
    }

    //если нужно отображать json данные из внешнего ресурса
    // mounted: function() {
    //   axios.get('https://jsonplaceholder.typicode.com/users?_limited=5')
    //       .then(response => {
    //         this.firstTableData = response.data;
    //         console.log(response);
    //       })
    //       .catch(error => {
    //         console.log(error);
    //       });
    // }
  }

</script>

