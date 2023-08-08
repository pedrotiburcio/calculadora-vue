<script setup>
    const props = defineProps(['editaNum1', 'editaOperacao', 'editaNum2', 'camposPreenchidos', 'realizaOperacao', 'resultado'])
</script>

<template>
    <form>
        <div class="row justify-content-center align-items-center mt-5">
            <div class="col-md-2 col-sm-4">
                <input @change="props.editaNum1" class="form-control" type="number" placeholder="Num1" required>
            </div>
            <div class="col-md-1 col-sm-2">
                <select @change="props.editaOperacao" class="form-control">
                    <option value=""></option>
                    <option value="adicao">+</option>
                    <option value="subtracao">-</option>
                    <option value="multiplicacao">x</option>
                    <option value="divisao">÷</option>
                </select>
            </div>
            <div class="col-md-2 col-sm-4">
                <input @change="props.editaNum2" class="form-control" type="number" placeholder="Num2" required>
            </div>
            <div class="col-md-1 col-sm-12">
                <span>=</span>
            </div>
            <div class="col-md-3 col-sm-6">
                <span v-if="!props.camposPreenchidos">
                </span>
                <span v-else-if="props.camposPreenchidos" :props.resultado="props.realizaOperacao" class="form-control cor-result">
                    {{ props.resultado }}
                </span>
            </div>
        </div>
    </form>
</template>

<style scoped>
input {
    background-color: rgb(252, 252, 186);
}

select {
    background-color: rgb(253, 183, 183);
}

input, select {
    font-size: 40px;
    text-align: center;
}

span {
    font-size: 40px;
}

.cor-result {
    background-color: rgb(154, 253, 171);
    color: #0c1077;
}

</style>