<template>
    <div ref='editor'></div>
    <button @click='syncHTML'>同步内容</button>
    <div :innerHTML='content.html'></div>
</template>



<script>
import WangEditor from 'wangeditor';

export default {
    data: () => ({
        $editor: null,
        content: {
            html: '',
        },
    }),
    mounted() {
        const editor = this.$refs.editor;
        const instance = new WangEditor(editor);
        Object.assign(instance.config, {
            onchange() {
                console.log('change');
            },
        });
        instance.create();
        this.$editor = instance;
    },

    methods: {
        syncHTML() {
            this.content.html = this.$editor.txt.html();
        },
    },
};
</script>
