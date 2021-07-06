<template>
    <div id="research" class="content research"> <!-- 元素id与配置文件中anchor.id一致 -->
        <!-- 标题 -->
        <ModuleHeader :title="research.header.title" :sub-title="research.header.subtitle"/>
        
        <!-- 自定义内容 -->
    <div>
    <a-collapse accordion>
      <a-collapse-panel key="1" header="研究方向 1">
        <p>{{ research.direct1 }}</p>
      </a-collapse-panel>
      <a-collapse-panel key="2" header="研究方向 2" :disabled="false">
        <p>{{ research.direct2 }}</p>
      </a-collapse-panel>
      <a-collapse-panel key="3" header="研究方向 3">
        <p>{{ research.direct3 }}</p>
      </a-collapse-panel>
    </a-collapse>
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
            research(): Module {
                // 使用getModule方法获取该模块的配置内容
                return this.$store.getters.getModule('research');
            },
        },
    })
    export default class Research extends Vue {
    }
</script>

<style scoped lang="scss">
    // 自定义样式
    @import '../styles/variable';

    .research {
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
