<template>
    <div class="memo-app">
        <memo-form @addMemo="addMemo" />
        <memo />
    </div>
</template>

<script>
import MemoForm from './MemoForm';
import Memo from './Memo';
export default {
    name: 'MemoApp',
    components: {
        MemoForm,
        Memo
    },
    data() {
        return{
            memos: [],
        }           
    },

    created() {
        this.memos = localStorage.memos ? JSON.parse(localStorage.memos) : [];
    },

    methods: {
        addMemo (payload) {
            this.memos.push(payload);
            this.storeMemo();
        },

        storeMemo () {
            const memoToString = JSON.stringify(this.memos);
            localStorage.setItem('memos', memoToString);
        }
    }
}
</script>