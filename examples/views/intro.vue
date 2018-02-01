<template>
    <l-generic>
        <div class="v-intro">
            <h1>ECharts 图表</h1>
            <p>一个使用 JavaScript 实现的开源可视化库，可以流畅的运行在 PC 和移动设备上，提供直观，交互丰富，可高度个性化定制的数据可视化图表。</p>

            <h2>柱状图</h2>
            <u-example title="尺寸">
                <template slot="case">
                    <e-charts :options="options.bar" style="width:100%;height:500px;" autoResize></e-charts>
                </template>
                <template slot="desc">
                    <p>通过设置<code>width</code>、<code>height</code>属性改变 ECharts 实例的尺寸。</p>
                    <p>如果未显示指定<code>width</code>、<code>height</code>属性，则会动态计算容器的宽高做 ECharts 实例的尺寸。</p>
                </template>
                <u-code slot="code" lang="html">{{codes.bar}}</u-code>
            </u-example>

            <h2>饼图</h2>
            <u-example title="自动重绘">
                <template slot="case">
                    <e-charts :options="options.pie" style="width:100%;height:500px;" autoResize></e-charts>
                </template>
                <template slot="desc">
                    <p>设置<code>autoResize</code>属性用来指定 ECharts 实例在组件根元素尺寸变化时是否需要自动进行重绘。</p>
                </template>
                <u-code slot="code" lang="html">{{codes.pie}}</u-code>
            </u-example>

            <div class="api">
                <h2>API</h2>
                <h3>属性</h3>
                <table>
                    <thead>
                        <tr>
                            <th>属性</th>
                            <th>说明</th>
                            <th>类型</th>
                            <th>默认值</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr>
                            <td>type</td>
                            <td>按钮类型，可选值为<code>primary</code>、<code>ghost</code>、<code>dashed</code>、<code>text</code>、<code>info</code>、<code>success</code>、<code>warning</code>、<code>error</code>或者不设置</td>
                            <td>String</td>
                            <td>-</td>
                        </tr>
                        <tr>
                            <td>size</td>
                            <td>按钮大小，可选值为<code>large</code>、<code>small</code>、<code>default</code>或者不设置</td>
                            <td>String</td>
                            <td>-</td>
                        </tr>
                        <tr>
                            <td>shape</td>
                            <td>按钮形状，可选值为<code>circle</code>或者不设置</td>
                            <td>String</td>
                            <td>-</td>
                        </tr>
                        <tr>
                            <td>long</td>
                            <td>开启后，按钮的长度为 100%</td>
                            <td>Boolean</td>
                            <td>false</td>
                        </tr>
                        <tr>
                            <td>html-type</td>
                            <td>设置<code>button</code>原生的<code>type</code>，可选值为<code>button</code>、<code>submit</code>、<code>reset</code></td>
                            <td>String</td>
                            <td>button</td>
                        </tr>
                        <tr>
                            <td>disabled</td>
                            <td>设置按钮为禁用状态</td>
                            <td>Boolean</td>
                            <td>false</td>
                        </tr>
                        <tr>
                            <td>loading</td>
                            <td>设置按钮为加载中状态</td>
                            <td>Boolean</td>
                            <td>false</td>
                        </tr>
                        <tr>
                            <td>icon</td>
                            <td>设置按钮的图标类型</td>
                            <td>String</td>
                            <td>-</td>
                        </tr>
                    </tbody>
                </table>
                
                <h3>事件</h3>
                <table>
                    <thead>
                        <tr>
                            <th>事件名</th>
                            <th>说明</th>
                            <th>返回值</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr>
                            <td>on-complete</td>
                            <td>动画播放完毕时触发</td>
                            <td>无</td>
                        </tr>
                    </tbody>
                </table>
            </div>
        </div>
    </l-generic>
</template>

<style lang="less" scoped>
.v-intro
{
    padding: 20px 25px;
}
</style>

<script lang="ts">
import { component, View } from "flagwind-web";
import ECharts from "src";
import * as codes from "examples/codes";
import * as options from "examples/options";

@component
({
    components:
    {
        "e-charts": ECharts
    }
})
export default class Intro extends View
{
    /**
     * 演示需要的代码。
     * @protected
     * @member
     * @returns any
     */
    protected codes: any = codes;

    /**
     * 演示需要的数据选项。
     * @protected
     * @member
     * @returns any
     */
    protected options: any = options;
}
</script>
