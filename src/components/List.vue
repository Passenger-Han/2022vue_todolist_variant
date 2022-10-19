<template>
<div class="container">
    <ul class="list">
        <template v-if="todoListData.length == 0">
                <li>
                    <div class="text">
                        <p>모든 일을 끝마쳤습니다!</p>
                    </div>
                    <div class="btns">
                        <button disabled>수정</button>
                        <button disabled>삭제</button>
                </div>
                </li>
            </template>
        <template v-for="(element, index) in todoListData" :key="index">
            <li>
                <div class="text">
                    <p>{{ index + 1 }}. {{ element }}</p>
                </div>                    
                <div class="btns">
                    <button disabled>
                        수정
                    </button>
                    <button @click="remove(element, index)">삭제</button>
                </div>
            </li>
        </template>
        <!-- SAMPLE -->
        <!-- <li>
            <div class="text">
                <p>Lorem ipsum dolor sit amet.</p>
            </div>
            <div class="btns">
                <button>수정</button>
                <button>삭제</button>
            </div>
        </li> -->
    </ul>
</div>
</template>

<script>
export default {
    props: [
        'todoListData',
    ],
    
    data(){
        return {

        };
    },

    methods: {
        remove: function(element, index){
            this.$emit('removeTodo', element, index);
        }
    },
}
</script>

<style lang="scss">
.list {
    display: flex;
    flex-direction: column;
    gap: 0.5rem;
    margin-bottom: 1rem;

    li {
        padding: 0.5rem;

        display: flex;
        justify-content: space-between;
        align-items: center;
        gap: 0.5rem;

        background: #EEE;
        color: #111;
        border: 1px solid #EEE;
        border-radius: 0.375rem;

        .text {
            flex-grow: 1;
            word-break: break-all;
        }

        .btns {
            flex-basis: 30%;
            flex-shrink: 0;

            display: flex;
            justify-content: space-between;
            gap: 0.25rem;

            button {
                background: #FFF;
                flex-grow: 1;
                padding: 0.375rem 0;
            }
        }
    }

    li.done {
        background: #000;
        color: #FFF;
        border: 1px solid #999;

        .text {
            text-decoration-line: line-through;
        }

        button {
            background: #000;
            color: #FFF;
            border: 1px solid #999;
        }
    }
}
</style>