<template>
    <div id="admission" class="content admission"> <!-- 元素id与配置文件中anchor.id一致 -->
        <!-- 标题 -->
        <ModuleHeader :title="admission.header.title" :sub-title="admission.header.subtitle"/>
        
        <!-- 自定义内容 -->
        <div>
            <h1>招生专业</h1>
            <span>080901-物理电子学</span>
            <span>085208-电子与通信工程</span>
            <span>085400-电子信息</span>
        </div>
        <div class="direct">
            <h1>招生方向</h1>
            <span>太赫兹电子学，高功率微波</span>
        </div>
    </div>
</template>

<script lang="ts">
    import {Component, Vue} from 'vue-property-decorator';
    import ModuleHeader from '@/components/module/ModuleHeader.vue';
    import {Module} from '@/api/user_interface';

    @Component({
        components: {
            ModuleHeader,
        },
        computed: {
            admission(): Module {
                // 使用getModule方法获取该模块的配置内容
                return this.$store.getters.getModule('admission');
            },
        },
    })
    export default class Admission extends Vue {
    }
</script>

<style scoped lang="scss">
    // 自定义样式
    @import '../styles/variable';

    .admission {
        .col {
            padding: 0 1rem;
        }

        .avatar {
            display: block;
            width: 100%;
            border-radius: 5px;
        }

        .title {
            letter-spacing: 5px;
            text-transform: uppercase;
        }

        .brief {
            display: block;
            margin: 1rem auto;
        }

        @media screen and (max-width: $--screen-md-min) {
            .col {
                padding: 0;
                &.color-content {
                    margin-top: 1.5rem;
                }
            }
        }

        .keys-row {
            margin: 1rem auto;

            .keys-col {
                margin: .5rem auto;
                word-break: break-all;
                padding-right: 1rem;

                .key {
                    margin-right: .5rem;
                    font-weight: bold;
                }

                .value {
                    color: inherit;
                    text-decoration: underline;
                }
            }
        }
    }
    h1{
        font-weight: bold;
        font-size: 24px;
    }
    
span{
    word-break:normal; 
    width:auto; 
    display:block; 
    white-space:pre-wrap;
    word-wrap : break-word ;
    overflow: hidden ;
    font-size: 16px;
}
.direct{
    margin-top: 10px;
}
</style>
