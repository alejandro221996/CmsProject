<script setup>
onMounted(() => {
  if (!localStorage.getItem("token")) {
    // redirect to home page
    window.location.href = "/auth/login";
  }
});
definePageMeta({
  layout: "custom",
});
</script>
<template>
    <div class="mt-8">
        <h1 class="text-3xl"> Published Pages</h1>
        <ag-grid-vue
            style="width: 1000px; height: 470px"
            class="ag-theme-alpine mt-8"
            :columnDefs="columnDefs"
            :rowData="rowData"
        >
        </ag-grid-vue>
    </div>
</template>

<script>
import "ag-grid-community/styles/ag-grid.css";
import "ag-grid-community/styles/ag-theme-alpine.css";
import { AgGridVue } from "ag-grid-vue3";
export default {
    components: {
        AgGridVue,
    },
    setup() {
        return {
        columnDefs: [
            { headerName: "Id", field: "id" },
            { headerName: "Descripcion", field: "description" },
            { headerName: "Usuario Creó", field: "user_creation" },
            { headerName: "Fecha Creación", field: "creation_date" },
            { headerName: "Usuario Modificó", field: "user_modify" },
            { headerName: "Fecha Modificación", field: "creation_date" },
            ],
            rowData: [
                { id: 1, description: "Page 1", user_creation: "User 1", creation_date: "2021-01-01", user_modify: "User 1", modify_date: "2021-01-01" },
                { id: 2, description: "Page 2", user_creation: "User 1", creation_date: "2021-01-01", user_modify: "User 1", modify_date: "2021-01-01" },
                { id: 3, description: "Page 3", user_creation: "User 1", creation_date: "2021-01-01", user_modify: "User 1", modify_date: "2021-01-01" },
                { id: 4, description: "Page 4", user_creation: "User 1", creation_date: "2021-01-01", user_modify: "User 1", modify_date: "2021-01-01" },
                { id: 5, description: "Page 5", user_creation: "User 1", creation_date: "2021-01-01", user_modify: "User 1", modify_date: "2021-01-01" },
                { id: 6, description: "Page 6", user_creation: "User 1", creation_date: "2021-01-01", user_modify: "User 1", modify_date: "2021-01-01" },
                { id: 7, description: "Page 7", user_creation: "User 1", creation_date: "2021-01-01", user_modify: "User 1", modify_date: "2021-01-01" },
                { id: 8, description: "Page 8", user_creation: "User 1", creation_date: "2021-01-01", user_modify: "User 1", modify_date: "2021-01-01" },
                { id: 9, description: "Page 9", user_creation: "User 1", creation_date: "2021-01-01", user_modify: "User 1", modify_date: "2021-01-01" },
                { id: 10, description: "Page 10", user_creation: "User 1", creation_date: "2021-01-01", user_modify: "User 1", modify_date: "2021-01-01" },
            ]
        };
    },

};

</script>
