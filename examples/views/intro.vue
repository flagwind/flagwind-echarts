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
                <h3>配置属性</h3>
                <table>
                    <thead>
                        <tr>
                            <th>属性名</th>
                            <th>说明</th>
                            <th>类型</th>
                            <th>必填</th>
                            <th>默认值</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr>
                            <td>width</td>
                            <td>ECharts 实例的宽度。</td>
                            <td>Number | String</td>
                            <td>-</td>
                            <td>-</td>
                        </tr>
                        <tr>
                            <td>height</td>
                            <td>ECharts 实例的高度。</td>
                            <td>Number | String</td>
                            <td>-</td>
                            <td>-</td>
                        </tr>
                        <tr>
                            <td>initOptions</td>
                            <td>
                                用于初始化 ECharts 实例的配置项，有下面几个可选项：<br />
                                <strong>devicePixelRatio:Number</strong> 设备像素比，默认取浏览器的值 window.devicePixelRatio；<br />
                                <strong>renderer:String</strong> 渲染器，支持 "canvas" 或者 "svg"。
                            </td>
                            <td>Object</td>
                            <td>-</td>
                            <td>-</td>
                        </tr>
                        <tr>
                            <td>options</td>
                            <td>所有参数和数据的修改都可以通过设置 options 完成，ECharts 会合并新的参数和数据，然后刷新图表；<br />
                            如果开启动画的话，ECharts 找到两组数据之间的差异然后通过合适的动画去表现数据的变化。</td>
                            <td>Object</td>
                            <td>yes</td>
                            <td>-</td>
                        </tr>
                        <tr>
                            <td>theme</td>
                            <td>可以是一个主题的配置对象，也可以是使用已经通过静态方法<code>registerTheme</code>注册的主题名称。</td>
                            <td>String | Object</td>
                            <td>-</td>
                            <td>-</td>
                        </tr>
                        <tr>
                            <td>group</td>
                            <td>图表的分组，用于联动。</td>
                            <td>String</td>
                            <td>-</td>
                            <td>-</td>
                        </tr>
                        <tr>
                            <td>autoResize</td>
                            <td>用于指示当窗口被调整大小时是否自动调整 ECharts 实例的大小。</td>
                            <td>Boolean</td>
                            <td>-</td>
                            <td>false</td>
                        </tr>
                        <tr>
                            <td>watchShallow</td>
                            <td>这个属性可以用来关闭对<code>options</code>属性的深度监听；<br />
                                对于有大量数据的图表，可能需要开启这个选项，让 Vue 仅监听<code>options</code>属性本身的变化而忽略内部属性的变化；<br />
                                如果开启了这个选项并且需要重绘图表时，需要重新设置<code>options</code>属性的直接引用，或者调用<code>mergeOptions</code>方法来手动管理图表内的数据。</td>
                            <td>Boolean</td>
                            <td>-</td>
                            <td>false</td>
                        </tr>
                    </tbody>
                </table>

                <h3>计算属性</h3>
                <table>
                    <thead>
                        <tr>
                            <th>属性名</th>
                            <th>说明</th>
                            <th>类型</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr>
                            <td>computedWidth</td>
                            <td>获取 ECharts 实例容器的宽度。</td>
                            <td>Number</td>
                        </tr>
                        <tr>
                            <td>computedHeight</td>
                            <td>获取 ECharts 实例容器的高度。</td>
                            <td>Number</td>
                        </tr>
                        <tr>
                            <td>isDisposed</td>
                            <td>表示 ECharts 实例是否已经被释放。</td>
                            <td>Boolean</td>
                        </tr>
                        <tr>
                            <td>computedOptions</td>
                            <td>获取 ECharts 实例维护的 options 对象。</td>
                            <td>Object</td>
                        </tr>
                    </tbody>
                </table>

                <h3>实例方法</h3>
                <table>
                    <thead>
                        <tr>
                            <th>方法名</th>
                            <th>说明</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr>
                            <td>mergeOptions</td>
                            <td>设置 ECharts 实例的配置项以及数据。</td>
                        </tr>
                        <tr>
                            <td>resize</td>
                            <td>改变图表尺寸，在容器大小发生改变时需要手动调用。</td>
                        </tr>
                        <tr>
                            <td>dispatchAction</td>
                            <td>触发图表行为，例如图例开关 legendToggleSelect, 数据区域缩放 dataZoom，显示提示框 showTip 等等，更多见 action 和 events 的文档。</td>
                        </tr>
                        <tr>
                            <td>convertToPixel</td>
                            <td>转换坐标系上的点到像素坐标值。</td>
                        </tr>
                        <tr>
                            <td>convertFromPixel</td>
                            <td>转换像素坐标值到逻辑坐标系上的点。是 convertToPixel 的逆运算。 具体实例可参考 convertToPixel。</td>
                        </tr>
                        <tr>
                            <td>containPixel</td>
                            <td>判断给定的点是否在指定的坐标系或者系列上。</td>
                        </tr>
                        <tr>
                            <td>showLoading</td>
                            <td>显示加载动画效果。可以在加载数据前手动调用改接口显示加载动画，在数据加载完成后调用 hideLoading 隐藏加载动画。</td>
                        </tr>
                        <tr>
                            <td>hideLoading</td>
                            <td>隐藏动画加载效果。</td>
                        </tr>
                        <tr>
                            <td>getDataUrl</td>
                            <td>导出图表图片，返回一个 base64 的 url。</td>
                        </tr>
                        <tr>
                            <td>getConnectedDataUrl</td>
                            <td>导出联动的图表图片，返回一个 base64 的 url。</td>
                        </tr>
                        <tr>
                            <td>clear</td>
                            <td>清空当前实例，会移除实例中所有的组件和图表。</td>
                        </tr>
                        <tr>
                            <td>dispose</td>
                            <td>销毁实例，销毁后实例无法再被使用。</td>
                        </tr>
                    </tbody>
                </table>

                <h3>静态方法</h3>
                <table>
                    <thead>
                        <tr>
                            <th>方法名</th>
                            <th>说明</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr>
                            <td>connect</td>
                            <td>多个图表实例实现联动。</td>
                        </tr>
                        <tr>
                            <td>disconnect</td>
                            <td>解除图表实例的联动，如果只需要移除单个实例，可以将通过将该图表实例 group 设为空。</td>
                        </tr>
                        <tr>
                            <td>registerTheme</td>
                            <td>注册主题，用于初始化实例的时候指定。</td>
                        </tr>
                        <tr>
                            <td>registerMap</td>
                            <td>注册可用的地图，必须在包括 geo 组件或者 map 图表类型的时候才能使用。</td>
                        </tr>
                        <tr>
                            <td>getMap</td>
                            <td>获取已注册的地图。</td>
                        </tr>
                    </tbody>
                </table>
                
                <h3>事件</h3>
                <table>
                    <thead>
                        <tr>
                            <th>事件名</th>
                            <th>说明</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr>
                            <td>click</td>
                            <td></td>
                        </tr>
                        <tr>
                            <td>dblclick</td>
                            <td></td>
                        </tr>
                        <tr>
                            <td>mouseover</td>
                            <td></td>
                        </tr>
                        <tr>
                            <td>mouseout</td>
                            <td></td>
                        </tr>
                        <tr>
                            <td>mousedown</td>
                            <td></td>
                        </tr>
                        <tr>
                            <td>mouseup</td>
                            <td></td>
                        </tr>
                        <tr>
                            <td>globalout</td>
                            <td></td>
                        </tr>
                        <tr>
                            <td>legendselectchanged</td>
                            <td>切换图例选中状态后的事件。</td>
                        </tr>
                        <tr>
                            <td>legendselected</td>
                            <td>图例选中后的事件。</td>
                        </tr>
                        <tr>
                            <td>legendunselected</td>
                            <td>图例取消选中后的事件。</td>
                        </tr>
                        <tr>
                            <td>legendscroll</td>
                            <td>图例滚动事件。</td>
                        </tr>
                        <tr>
                            <td>datazoom</td>
                            <td>数据区域缩放后的事件。</td>
                        </tr>
                        <tr>
                            <td>datarangeselected</td>
                            <td>视觉映射组件中，range 值改变后触发的事件。</td>
                        </tr>
                        <tr>
                            <td>timelinechanged</td>
                            <td>时间轴中的时间点改变后的事件。</td>
                        </tr>
                        <tr>
                            <td>timelineplaychanged</td>
                            <td>时间轴中播放状态的切换事件。</td>
                        </tr>
                        <tr>
                            <td>restore</td>
                            <td>重置 option 事件。</td>
                        </tr>
                        <tr>
                            <td>dataviewchanged</td>
                            <td>工具栏中数据视图的修改事件。</td>
                        </tr>
                        <tr>
                            <td>magictypechanged</td>
                            <td>工具栏中动态类型切换的切换事件。</td>
                        </tr>
                        <tr>
                            <td>geoselectchanged</td>
                            <td>geo 中地图区域切换选中状态的事件。</td>
                        </tr>
                        <tr>
                            <td>geoselected</td>
                            <td>geo 中地图区域选中后的事件。</td>
                        </tr>
                        <tr>
                            <td>geounselected</td>
                            <td>geo 中地图区域取消选中后的事件。</td>
                        </tr>
                        <tr>
                            <td>pieselectchanged</td>
                            <td>series-pie 中饼图扇形切换选中状态的事件。</td>
                        </tr>
                        <tr>
                            <td>pieselected</td>
                            <td>series-pie 中饼图扇形选中后的事件。</td>
                        </tr>
                        <tr>
                            <td>pieunselected</td>
                            <td>series-pie 中饼图扇形取消选中后的事件。</td>
                        </tr>
                        <tr>
                            <td>mapselectchanged</td>
                            <td>series-map 中地图区域切换选中状态的事件。</td>
                        </tr>
                        <tr>
                            <td>mapselected</td>
                            <td>series-map 中地图区域选中后的事件。</td>
                        </tr>
                        <tr>
                            <td>mapunselected</td>
                            <td>series-map 中地图区域取消选中后的事件。</td>
                        </tr>
                        <tr>
                            <td>axisareaselected</td>
                            <td>平行坐标轴 (Parallel)范围选取事件。</td>
                        </tr>
                        <tr>
                            <td>focusnodeadjacency</td>
                            <td>graph的邻接节点高亮事件。</td>
                        </tr>
                        <tr>
                            <td>unfocusnodeadjacency</td>
                            <td>graph的邻接节点取消高亮事件。</td>
                        </tr>
                        <tr>
                            <td>brush</td>
                            <td>选框添加事件。即发出 brush action 得到的事件。</td>
                        </tr>
                        <tr>
                            <td>brushselected</td>
                            <td>对外通知当前选中了什么。</td>
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
