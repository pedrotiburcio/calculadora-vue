<script setup>
    const props = defineProps(['editaNum1', 'editaOperacao', 'editaNum2', 'camposPreenchidos', 'realizaOperacao', 'resultado'])
</script>

<template>
    <form>
        <div class="row d-flex justify-content-center align-items-center mt-5">
            <div class="col-md-4 col-9">
                <input @change="props.editaNum1" class="form-control" type="number" placeholder="Num1" required>
            </div>
            <div class="col-md-2 col-4 mt-1">
                <select @change="props.editaOperacao" class="form-control">
                    <option value=""></option>
                    <option value="adicao">+</option>
                    <option value="subtracao">-</option>
                    <option value="multiplicacao">x</option>
                    <option value="divisao">÷</option>
                </select>
            </div>
            <div class="col-md-4 col-9 mt-1">
                <input @change="props.editaNum2" class="form-control" type="number" placeholder="Num2" required>
            </div>
            <div class="col-md-10 col-8 mt-1">
                <span>=</span>
            </div>
            <div class="col-md-7 col-12 mt-1">
                <span v-if="!props.camposPreenchidos">
                </span>
                <input readonly v-else-if="props.camposPreenchidos" :props.resultado="props.realizaOperacao" class="form-control cor-result mt-3" :value="props.resultado"/>
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

input, select, span {
    font-size: 40px;
    text-align: center;
}

.cor-result {
    background-color: rgb(154, 253, 171);
    color: #0c1077;
}

@media (max-width: 640px) {
    input, select, span {
        font-size: 24px;
    }
}

</style>