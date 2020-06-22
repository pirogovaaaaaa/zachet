<template>
    <div id="app">
        <div class="container">
        <h1 v-if="error">{{ error }}</h1>
        <div class="form-group">
            <label for> Наименование </label>
            <input type="text" class="form-control" v-model="name" placeholder="Название_товара"/>
            <label for> Количество </label>
            <input type="text" class="form-control" v-model="quantity" placeholder="0"/>
            <button class="btn btn-primary mt-2" @click="onSave"> Сохранить </button>
            <hr />
        </div>
            <table style="margin : 0px 0px 0px 20px" class="table-striped table-bordered">
                <thead class="thead-dark">
            <tr >
                <th align=left scope="row"> Наименование</th>
                <th align=right scope="row"> Количество</th>
            </tr>

                </thead>
        <tr class="row mt-2" v-for="(list) in items" :key="list.id">
                <th align=left scope="row"> {{list.name}}</th>
                <th align=right scope="row"> {{list.quantity}}</th>
        </tr>
            </table>
    </div>
    </div>
</template>

<script>
export default {
    name: "App",
    data: function() {
        return {
            items : [],
            name : "",
            quantity : "",
            id : 0,
            error : "",
            isEditMode : false
        };
    },
    components: {},
    methods: {
        async updateData() {
            try{
                let result = await this.$http.get("http://localhost:3000/items");
                this.items = await result.json();
                this. error = "";
            } catch(exception) {
                console.error(exception);
            }
        },
        async onSave() {
            let list = {
                name: this.name,
                quantity: this.quantity,
            };
            try {
                await this.$http.post("http://localhost:3000/items", list);
                this.updateData();
            } catch(e) {
                console.error(e);
            }
        }
    },
    created() {
        this.updateData();
    }
};
</script>