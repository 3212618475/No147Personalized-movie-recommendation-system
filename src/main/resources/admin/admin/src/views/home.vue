<template>
<div class="content" :style='{"minHeight":"100vh","width":"100%","padding":"30px","background":"url(http://codegen.caihongy.cn/20221201/89fef0fbf1554570bdd4d30adf9e9465.png) no-repeat center 40px","height":"auto"}'>
	<div class="text" :style='{"margin":"30px auto","color":"#fff","textAlign":"center","background":"none","width":"100%","fontSize":"32px","lineHeight":"600px","fontWeight":"bold","height":"600px"}'>欢迎使用 {{this.$project.projectName}}</div>
</div>
</template>
<script>
//0
import router from '@/router/router-static'
import * as echarts from 'echarts'
export default {
	data() {
		return {
		};
	},
  mounted(){
    this.init();
  },
  methods:{
    init(){
        if(this.$storage.get('Token')){
        this.$http({
            url: `${this.$storage.get('sessionTable')}/session`,
            method: "get"
        }).then(({ data }) => {
            if (data && data.code != 0) {
            router.push({ name: 'login' })
            }
        });
        }else{
            router.push({ name: 'login' })
        }
    },
  }
};
</script>
<style lang="scss" scoped>
    .cardView {
        display: flex;
        flex-wrap: wrap;
        width: 100%;

        .cards {
            display: flex;
            align-items: center;
            width: 100%;
            margin-bottom: 10px;
            justify-content: center;
            .card {
                width: calc(25% - 20px);
                margin: 0 10px;
                /deep/.el-card__body{
                    padding: 0;
                }
            }
        }
    }
</style>
