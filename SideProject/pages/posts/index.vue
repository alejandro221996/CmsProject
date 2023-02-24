<script setup>
    onBeforeMount(() => {
        if (!localStorage.getItem("token")) {
            // redirect to home page
            window.location.href = "/auth/login";
        }
    });
</script >
<template>
    <div class="mt-8">
    <h1 class="text-3xl">Posts</h1>
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
        //function to redirect to home page if token is not present   
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
            { id: 1, description: "Post 1", user_creation: "User 1", creation_date: "2021-01-01", user_modify: "User 1", modify_date: "2021-01-01" },
            { id: 2, description: "Post 2", user_creation: "User 1", creation_date: "2021-01-01", user_modify: "User 1", modify_date: "2021-01-01" },
            { id: 3, description: "Post 3", user_creation: "User 1", creation_date: "2021-01-01", user_modify: "User 1", modify_date: "2021-01-01" },
            { id: 4, description: "Post 4", user_creation: "User 1", creation_date: "2021-01-01", user_modify: "User 1", modify_date: "2021-01-01" },
            { id: 5, description: "Post 5", user_creation: "User 1", creation_date: "2021-01-01", user_modify: "User 1", modify_date: "2021-01-01" },
            { id: 6, description: "Post 6", user_creation: "User 1", creation_date: "2021-01-01", user_modify: "User 1", modify_date: "2021-01-01" },
            { id: 7, description: "Post 7", user_creation: "User 1", creation_date: "2021-01-01", user_modify: "User 1", modify_date: "2021-01-01" },
            { id: 8, description: "Post 8", user_creation: "User 1", creation_date: "2021-01-01", user_modify: "User 1", modify_date: "2021-01-01" },
            { id: 9, description: "Post 9", user_creation: "User 1", creation_date: "2021-01-01", user_modify: "User 1", modify_date: "2021-01-01" },
            { id: 10, description: "Post 10", user_creation: "User 1", creation_date: "2021-01-01", user_modify: "User 1", modify_date: "2021-01-01" },
            ],
        redirect,
        };
    }, 

};

definePageMeta ({
    layout: 'custom',
})

</script>

