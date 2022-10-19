<template>
<div class="container">
    <h1>TODO LIST</h1>
    <!-- <div class="input-wrapper">
        <input type="text" name="todoinput" id="todoinput" placeholder="여기에 할 일을 입력.." v-model="todoinput">
        <button @click="submit">등록</button>
    </div> -->
    <form action="javascript:void(0);" class="input-wrapper">
        <input type="text" name="todoinput" id="todoinput" placeholder="여기에 할 일을 입력.." v-model="todoinput">
        <button @click="submit">등록</button>
    </form>
</div>
</template>

<script>
export default {
    data(){
        return {
            todoinput: '',
        }
    },

    methods: {
        submit: function(){
            if (this.todoinput == ''){
                alert('할 일을 적지 않아 아무것도 등록하지 못했습니다.');
            } else {
                let trimed = this.todoinput && this.todoinput.trim(); // 할 일의 내용
                this.$emit('submitTodo', trimed);
                this.todoinput = '';
            }
        }
    },
}
</script>

<style scoped lang="scss">
h1 {letter-spacing: -0.0625rem; margin-bottom: 0.5rem;}
.input-wrapper {
    display: flex;
    justify-content: space-between;
    gap: 0.5rem;

    margin-bottom: 1rem;

    input, button {
        padding: 0.75rem;
    }

    input {
        flex-grow: 1;

        border: none;
        outline: none;
        border-radius: 0.375rem;
    }

    button {
        flex-basis: 15%;
        flex-shrink: 0;

        border-radius: 0.375rem;
    }
}
</style>