<template>
    <div class="container" @click.stop="selectF()">
        <slot></slot>
    </div>
</template>

<script>
export default {
    name: "AnSelectCheckbox",
    props: {'index_': Number | String, 'select_index_': Number | String, 'data_': Array},
    data() {
        return {
            index: 0, //所属下标
            data: '',
            select_index: -1,
        }
    },
    watch: {
        select_index_(val) {
            this.select_index = val;
        },
        index_(v) {
            this.index = v;
        },
        data_(v) {
            this.data = v;
        }
    },
    methods: {
        selectF() {
            this.$emit('AnSelectCheckboxF', {'index': this.index});
        }
    },
    created() {
    },
    mounted() {
        if (this.index_) {
            this.index = this.index_;
        }
        if (this.data_) {
            this.data = this.data_;
        }
    },
    destroyed() {
    }
}
</script>

<style scoped lang="scss">
.content {
    display: inline-block;
}
</style>
