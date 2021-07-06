<template>
    <div id="course" class="content course"> <!-- 元素id与配置文件中anchor.id一致 -->
        <!-- 标题 -->
        <ModuleHeader :title="course.header.title" :sub-title="course.header.subtitle"/>
        
        <!-- 自定义内容 -->
    <div style="background-color: #ececec; padding: 20px;">
    <a-row :gutter="16">
      <a-col :span="12">
        <a-card title="太赫兹真空电子学器件的原理与技术" :bordered="false">
          <p>介绍</p>
        </a-card>
      </a-col>
      <a-col :span="12">
        <a-card title="微纳加工技术及其太赫兹科学技术中的应用" :bordered="false">
          <p>介绍</p>
        </a-card>
      </a-col>
    </a-row>
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
            course(): Module {
                // 使用getModule方法获取该模块的配置内容
                return this.$store.getters.getModule('course');
            },
        },
    })
    export default class Course extends Vue {
    }
</script>

<style scoped lang="scss">
    // 自定义样式
    @import '../styles/variable';

    .course {
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
</style>
