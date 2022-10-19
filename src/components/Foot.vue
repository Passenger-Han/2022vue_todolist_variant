<template>
<div class="container button" @click="removeAll">
    전체 삭제
</div>
</template>

<script>
export default {
    methods: {
        removeAll: function(){
            this.$emit('removeAllTodo');
        },
    },
}
</script>

<style scoped lang="scss">
.button {
    padding: 0.75rem 0;
    width: 100%;

    background: #667;
    border-radius: 0.375rem;
    text-align: center;
}
</style>