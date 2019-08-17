<template>
    <div class="memo-form">
        <form @submit.prevent="addMemo">
            <fieldset>
                <div>
                    <input type="text" class="memo-form__title-form" placeholder="메모의 제목을 입력해주세요" v-model="title" />
                    <textarea class="memo-form__content-form" placeholder="메모의 내용을 입력해주세요" v-model="content" />
                    <button type="reset"><i class="fas fa-sync-alt"></i></button>
                </div>
                <button type="submit">등록하기</button>
            </fieldset>
        </form>
    </div>
</template>

<script>
export default {
    name: "MemoForm",
    data () {
        return {
            title: '',
            content: ''
        }
    },
    methods: {
        addMemo() {
            const { title, content } = this;
            const id = new Date().getTime();

            const isEmpty = title.length <= 0 || content.length <= 0;
            if (isEmpty) {
                return false;
            }

            this.$emit('addMemo', {id, title, content})
        }
    }
}
</script>

<style lang="scss" scoped>
.memo-form {
    margin-bottom: 24px;
    padding-bottom: 40px;
    border-bottom: 1px solid #eee;

    form {
        fieldset {
            border: none;
            div {
                position: relative;
                padding: 24px;
                margin-bottom: 20px;
                box-shadow: 0 4px 10px -4px rgba(0, 0, 0, 0.2);
                background: #fff;

                button[type="reset"] {
                    position: absolute;
                    right: 20px;
                    bottom: 20px;
                    font-size: 16px;
                    background: none;
                }

                
            }

            button[type="submit"] {
                float: right;
                width: 96px;
                padding: 12px 0;
                border-radius: 4px;
                background-color: #ff5a00;
                color: #fff;
                font-size: 16px;
            }
        }
    }

    &__title-form {
        width: 100%;
        margin-bottom: 12px;
        font-size: 18px;
        line-height: 26px;
        border: none;
    }

    &__content-form {
        width: 100%;
        height: 66px;
        font-size: 14px;
        line-height: 22px;
        vertical-align: top;
    }

    input:focus {
        outline: none;
    }
}
</style>