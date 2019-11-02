<template>
    <ag-grid-vue style="width: 500px; height: 500px;"
                 class="ag-theme-balham"
                 :columnDefs="columnDefs"
                :pivotGroupHeaderHeight="pivotGroupHeaderHeight"
                :groupHeaderHeight= "groupHeaderHeight"
                 :headerHeight="headerHeight"
                 :rowData="rowData">
    </ag-grid-vue>
</template>




<script>
    import {AgGridVue} from "ag-grid-vue";

    export default {
        name: 'App',
        data() {
            return {
                columnDefs: null,
                rowData: null,
                pivotGroupHeaderHeight:null,
                groupHeaderHeight:null,
                headerHeight:null,
            
            }
        },
        components: {
            AgGridVue
        },
        beforeMount() {
              this.columnDefs = [
        {headerName: 'Make', field: 'make', cellClass:'cell-wrap-text'},
        {headerName: 'Model', field: 'model',cellClass:'cell-wrap-text'},
        {headerName: 'Pricedfadfadfa', field: 'price',cellClass:'cell-wrap-text'}
    ];  
        this.groupHeaderHeight=60
        // this set the header height of the column
        this.headerHeight=80
        this.pivotGroupHeaderHeight=70
    fetch('https://api.myjson.com/bins/15psn9')
        .then(result => result.json())
        .then(rowData => this.rowData = rowData);        }
    }
</script>



<style lang="scss">
  @import "../node_modules/ag-grid-community/dist/styles/ag-grid.css";
  @import "../node_modules/ag-grid-community/dist/styles/ag-theme-balham.css";
</style>
<style>
      /* Display vertical css styling  */
.ag-header-cell-label .ag-header-cell-text{
    /*Force the width corresponding at how much width
    we need once the text is layed out vertically*/
    height: 70px;
    width: 50px;
    writing-mode:vertical-rl;;
    text-orientation: mixed;
    margin-top: 2px;
    align-self: auto;
  transform: rotate(-180deg);

}

</style>