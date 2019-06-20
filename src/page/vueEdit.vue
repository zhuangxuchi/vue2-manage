
<template>
    <div>
        <head-top></head-top>
        <div class="edit_container">
            <quill-editor 
                class="editer"
                v-model="content" 
                ref="myQuillEditor" 
                :options="editorOption" 
                @ready="onEditorReady($event)">
            </quill-editor>
        </div>
        <div class="submit_btn">
            <el-button type="primary" @click="submit">提交<i class="el-icon-check el-icon--right"></i></el-button>
        </div>
    </div>
</template>
<script>
import headTop from '../components/headTop'
import { quillEditor } from "vue-quill-editor"; //调用编辑器
export default {
    data() {
        return {
            content: '<h1>文本编辑</h1>',
            editorOption: {}
        }
    },
    components: {
        quillEditor,
        headTop
    },
    methods: {
        onEditorReady(editor) { // 准备编辑器
            console.log('editor ready!', editor)
        },
        submit(){
            console.log(this.content);
            this.$message.success('提交成功！')
        }
    },
    computed: {
        editor() {
            return this.$refs.myQuillEditor.quill;
        },
    }
}
</script>

<style lang="less">
	@import '../style/mixin';
	.edit_container{
		padding: 40px;
		margin-bottom: 40px;
	}
	.editer{
		height: 350px;
	}
	.submit_btn{
		text-align: center;
	}
</style>