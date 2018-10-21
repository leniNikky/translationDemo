<template>
    <div id="translateForm" class="row">
        <div class="col-md-6 col-md-offset-3">
        <form v-on:submit="formSubmit" class="well form-inline">
            <input type='text' v-model="translateText" placeholder="请输入要翻译的内容" class="form-control">
            <select v-model='language' class="form-control">
                <option value="en">English</option>
                <option value="fr">French</option>
                <option value="ja">Japanese</option>
                <option value="ko">Korean</option>
            </select>
            <input type='submit' value='翻译' class="btn btn-primary">
        </form>
        </div>
    </div>
</template>
<script>
export default {
    name:'TranslateForm',
    data:function(){
        return{
            translateText:"",
            language:"en"
        }
    },
    methods:{
        formSubmit:function(e){
            //alert(this.translateText)
            this.$emit("formsubmit",this.translateText,this.language);
            e.preventDefault();
            
        }
    }
}
</script>
<style>

</style>


