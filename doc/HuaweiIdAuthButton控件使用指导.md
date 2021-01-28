# HuaweiIdAuthButton控件使用指导<a name="ZH-CN_TOPIC_0000001073526079"></a>

-   [概述](#section136641412155918)
-   [开发准备](#section1910304925914)
-   [使用指导](#section18442122012100)
-   [通过布局xml文件使用](#section12327542111)
-   [通过Java或Kotlin代码创建实例](#section1158951810389)

## 概述<a name="section136641412155918"></a>

HuaweiIdAuthButton是华为帐号提供的一个按钮控件，此控件展示华为风格的登录按钮，可以让您方便快速地实现符合[华为帐号登录图标使用规范](华为帐号登录图标使用规范.md)的登录按钮。此控件只处理按钮的显示效果，如果要触发登录动作，请使用setOnClickListener\(OnClickListener\)注册一个监听器。

## 开发准备<a name="section1910304925914"></a>

按[开发准备](配置AppGallery-Connect.md)中的步骤[配置AppGallery Connect](配置AppGallery-Connect.md)并[集成HMS Core SDK](集成HMS-Core-SDK.md)之后即可使用HuaweiIdAuthButton。

>![](public_sys-resources/icon-note.gif) **说明：** 
>HuaweiIdAuthButton要求HMS Core SDK版本为4.0.0.300及以上。

## 使用指导<a name="section18442122012100"></a>

HuaweiIdAuthButton和一般的控件一样，有两种使用方式，一种是在布局xml文件中进行声明，另外一种是在Java或Kotlin代码中创建HuaweiIdAuthButton类的实例，并动态添加到布局中，您可以根据自己的需要选择使用。

## 通过布局xml文件使用<a name="section12327542111"></a>

**控件声明**

首先按以下方式声明HuaweiIdAuthButton控件：

```
<com.huawei.hms.support.hwid.ui.HuaweiIdAuthButton
     android:layout_width="wrap_content"
     android:layout_height="wrap_content"
/>
```

**界面示例**

![](figures/12.png)

>![](public_sys-resources/icon-caution.gif) **注意：** 
>按钮文本请使用“华为帐号登录”，不可随意更改。

在布局文件中声明控件后，还需要在Java或Kotlin代码中使用setOnClickListener\(OnClickListener\)注册一个监听器，在监听事件中执行登录操作。

**自定义参数**

HuaweiIdAuthButton提供了以下几种自定义样式参数：

<a name="table1464624591217"></a>
<table><thead align="left"><tr id="row15646184516121"><th class="cellrowborder" valign="top" width="25.192519251925194%" id="mcps1.1.4.1.1"><p id="p1864717456122"><a name="p1864717456122"></a><a name="p1864717456122"></a>自定义参数名</p>
</th>
<th class="cellrowborder" valign="top" width="30.893089308930893%" id="mcps1.1.4.1.2"><p id="p664794514124"><a name="p664794514124"></a><a name="p664794514124"></a>可选值</p>
</th>
<th class="cellrowborder" valign="top" width="43.91439143914391%" id="mcps1.1.4.1.3"><p id="p20647134541211"><a name="p20647134541211"></a><a name="p20647134541211"></a>说明</p>
</th>
</tr>
</thead>
<tbody><tr id="row16471445171218"><td class="cellrowborder" rowspan="2" valign="top" width="25.192519251925194%" headers="mcps1.1.4.1.1 "><p id="p964714571214"><a name="p964714571214"></a><a name="p964714571214"></a>hwid_button_theme</p>
</td>
<td class="cellrowborder" valign="top" width="30.893089308930893%" headers="mcps1.1.4.1.2 "><p id="p26471245141217"><a name="p26471245141217"></a><a name="p26471245141217"></a>hwid_button_theme_full_title</p>
</td>
<td class="cellrowborder" valign="top" width="43.91439143914391%" headers="mcps1.1.4.1.3 "><p id="p16647184551213"><a name="p16647184551213"></a><a name="p16647184551213"></a>按钮展示为图标+文字。</p>
</td>
</tr>
<tr id="row19647045171219"><td class="cellrowborder" valign="top" headers="mcps1.1.4.1.1 "><p id="p106471745171215"><a name="p106471745171215"></a><a name="p106471745171215"></a>hwid_button_theme_no_title</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.1.4.1.2 "><p id="p20647945181211"><a name="p20647945181211"></a><a name="p20647945181211"></a>按钮不展示文字。</p>
</td>
</tr>
<tr id="row8647145141219"><td class="cellrowborder" rowspan="6" align="left" valign="top" width="25.192519251925194%" headers="mcps1.1.4.1.1 "><p id="p1764711458128"><a name="p1764711458128"></a><a name="p1764711458128"></a>hwid_color_policy</p>
</td>
<td class="cellrowborder" valign="top" width="30.893089308930893%" headers="mcps1.1.4.1.2 "><p id="p764774512123"><a name="p764774512123"></a><a name="p764774512123"></a>hwid_color_policy_blue</p>
</td>
<td class="cellrowborder" valign="top" width="43.91439143914391%" headers="mcps1.1.4.1.3 "><p id="p1264714521214"><a name="p1264714521214"></a><a name="p1264714521214"></a>按钮颜色风格为蓝色，只有hwid_button_theme= hwid_button_theme_full_title时可用。</p>
</td>
</tr>
<tr id="row186477458129"><td class="cellrowborder" valign="top" headers="mcps1.1.4.1.1 "><p id="p106471459122"><a name="p106471459122"></a><a name="p106471459122"></a>hwid_color_policy_black</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.1.4.1.2 "><p id="p1064774541215"><a name="p1064774541215"></a><a name="p1064774541215"></a>按钮颜色风格为黑色。</p>
</td>
</tr>
<tr id="row17307444141"><td class="cellrowborder" valign="top" headers="mcps1.1.4.1.1 "><p id="p13144411148"><a name="p13144411148"></a><a name="p13144411148"></a>hwid_color_policy_gray</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.1.4.1.2 "><p id="p5317449147"><a name="p5317449147"></a><a name="p5317449147"></a>按钮颜色风格为灰色，只有hwid_button_theme= hwid_button_theme_full_title时可用。</p>
</td>
</tr>
<tr id="row49742044111510"><td class="cellrowborder" valign="top" headers="mcps1.1.4.1.1 "><p id="p09741144101512"><a name="p09741144101512"></a><a name="p09741144101512"></a>hwid_color_policy_red</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.1.4.1.2 "><p id="p20974134419158"><a name="p20974134419158"></a><a name="p20974134419158"></a>按钮颜色风格为红色。</p>
</td>
</tr>
<tr id="row1328502320166"><td class="cellrowborder" valign="top" headers="mcps1.1.4.1.1 "><p id="p1128662318168"><a name="p1128662318168"></a><a name="p1128662318168"></a>hwid_color_policy_white</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.1.4.1.2 "><p id="p142862230167"><a name="p142862230167"></a><a name="p142862230167"></a>按钮颜色风格为白色。</p>
</td>
</tr>
<tr id="row1634312111178"><td class="cellrowborder" valign="top" headers="mcps1.1.4.1.1 "><p id="p133445113175"><a name="p133445113175"></a><a name="p133445113175"></a>hwid_color_policy_white_with_border</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.1.4.1.2 "><p id="p23445119179"><a name="p23445119179"></a><a name="p23445119179"></a>按钮颜色风格为带描边白色，只有hwid_button_theme= hwid_button_theme_full_title时可用。</p>
</td>
</tr>
<tr id="row189351944111816"><td class="cellrowborder" rowspan="3" valign="top" width="25.192519251925194%" headers="mcps1.1.4.1.1 "><p id="p109364444180"><a name="p109364444180"></a><a name="p109364444180"></a>hwid_corner_radius</p>
</td>
<td class="cellrowborder" valign="top" width="30.893089308930893%" headers="mcps1.1.4.1.2 "><p id="p1293684417180"><a name="p1293684417180"></a><a name="p1293684417180"></a>hwid_corner_radius_large</p>
</td>
<td class="cellrowborder" valign="top" width="43.91439143914391%" headers="mcps1.1.4.1.3 "><p id="p1593664401814"><a name="p1593664401814"></a><a name="p1593664401814"></a>按钮圆角设置，大圆角。</p>
</td>
</tr>
<tr id="row067775121920"><td class="cellrowborder" valign="top" headers="mcps1.1.4.1.1 "><p id="p1267818561916"><a name="p1267818561916"></a><a name="p1267818561916"></a>hwid_corner_radius_medium</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.1.4.1.2 "><p id="p46781561916"><a name="p46781561916"></a><a name="p46781561916"></a>按钮圆角设置，中等圆角。</p>
</td>
</tr>
<tr id="row1034941021917"><td class="cellrowborder" valign="top" headers="mcps1.1.4.1.1 "><p id="p113499108195"><a name="p113499108195"></a><a name="p113499108195"></a>hwid_corner_radius_small</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.1.4.1.2 "><p id="p7349111001913"><a name="p7349111001913"></a><a name="p7349111001913"></a>按钮圆角设置，小圆角。</p>
</td>
</tr>
</tbody>
</table>

在布局文件引用命名空间：

```
xmlns:app="http://schemas.android.com/apk/res-auto"
```

自定义参数使用示例：

```
<com.huawei.hms.support.hwid.ui.HuaweiIdAuthButton
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    app:hwid_button_theme="hwid_button_theme_full_title"
    app:hwid_color_policy="hwid_color_policy_blue"
    app:hwid_corner_radius="hwid_corner_radius_large"
/>
```

**界面示例**

![](figures/10.png)

>![](public_sys-resources/icon-caution.gif) **注意：** 
>按钮文本请使用“华为帐号登录”，不可随意更改。

## 通过Java或Kotlin代码创建实例<a name="section1158951810389"></a>

**控件声明**

通过HuaweiIdAuthButton的构造函数可以创建对应实例，并通过addView的方式把HuaweiIdAuthButton加入到布局中。

<a name="table760914275399"></a>
<table><thead align="left"><tr id="row1660932783913"><th class="cellrowborder" valign="top" width="50%" id="mcps1.1.3.1.1"><p id="p126101527193912"><a name="p126101527193912"></a><a name="p126101527193912"></a>构造函数</p>
</th>
<th class="cellrowborder" valign="top" width="50%" id="mcps1.1.3.1.2"><p id="p1361032716392"><a name="p1361032716392"></a><a name="p1361032716392"></a>说明</p>
</th>
</tr>
</thead>
<tbody><tr id="row1461082711391"><td class="cellrowborder" valign="top" width="50%" headers="mcps1.1.3.1.1 "><p id="p76101271392"><a name="p76101271392"></a><a name="p76101271392"></a>HuaweiIdAuthButton(Context context)</p>
</td>
<td class="cellrowborder" valign="top" width="50%" headers="mcps1.1.3.1.2 "><p id="p17610127123914"><a name="p17610127123914"></a><a name="p17610127123914"></a>构造方法，创建HuaweiIdAuthButton实例。</p>
</td>
</tr>
<tr id="row13610427153916"><td class="cellrowborder" valign="top" width="50%" headers="mcps1.1.3.1.1 "><p id="p1761052714391"><a name="p1761052714391"></a><a name="p1761052714391"></a>HuaweiIdAuthButton(Context context, AttributeSet attributeSet)</p>
</td>
<td class="cellrowborder" valign="top" width="50%" headers="mcps1.1.3.1.2 "><p id="p206107271396"><a name="p206107271396"></a><a name="p206107271396"></a>构造方法，创建HuaweiIdAuthButton实例，根据属性集加载样式。</p>
</td>
</tr>
<tr id="row361317193405"><td class="cellrowborder" valign="top" width="50%" headers="mcps1.1.3.1.1 "><p id="p1661461924011"><a name="p1661461924011"></a><a name="p1661461924011"></a>HuaweiIdAuthButton(Context context, AttributeSet attributeSet, int defStyleAttr)</p>
</td>
<td class="cellrowborder" valign="top" width="50%" headers="mcps1.1.3.1.2 "><p id="p17614201914010"><a name="p17614201914010"></a><a name="p17614201914010"></a>构造方法，创建HuaweiIdAuthButton实例，可以指定默认样式。</p>
</td>
</tr>
</tbody>
</table>

**示例代码**

```
Java
HuaweiIdAuthButton huaweiIdAuthButton = new HuaweiIdAuthButton(this);
LinearLayout layout = findViewById(R.id.layout_sign_in_api);
layout.addView(huaweiIdAuthButton);
```

```
Kotlin
val huaweiIdAuthButton = HuaweiIdAuthButton(this)
val layout = findViewById<LinearLayout>(R.id.layout_sign_in_api)
layout.addView(huaweiIdAuthButton)
```

**自定义参数**

HuaweiIdAuthButton提供了以下几种自定义样式参数：

<a name="table31951129134217"></a>
<table><thead align="left"><tr id="row5195629154220"><th class="cellrowborder" valign="top" width="30.403040304030405%" id="mcps1.1.4.1.1"><p id="p1719513292429"><a name="p1719513292429"></a><a name="p1719513292429"></a>自定义参数方法</p>
</th>
<th class="cellrowborder" valign="top" width="36.26362636263626%" id="mcps1.1.4.1.2"><p id="p319519292424"><a name="p319519292424"></a><a name="p319519292424"></a>可选值</p>
</th>
<th class="cellrowborder" valign="top" width="33.33333333333333%" id="mcps1.1.4.1.3"><p id="p6195829104219"><a name="p6195829104219"></a><a name="p6195829104219"></a>说明</p>
</th>
</tr>
</thead>
<tbody><tr id="row219518294428"><td class="cellrowborder" rowspan="2" valign="top" width="30.403040304030405%" headers="mcps1.1.4.1.1 "><p id="p181951290427"><a name="p181951290427"></a><a name="p181951290427"></a>setTheme(int theme)</p>
</td>
<td class="cellrowborder" valign="top" width="36.26362636263626%" headers="mcps1.1.4.1.2 "><p id="p15195029174210"><a name="p15195029174210"></a><a name="p15195029174210"></a>HuaweiIdAuthButton.THEME_FULL_TITLE</p>
</td>
<td class="cellrowborder" valign="top" width="33.33333333333333%" headers="mcps1.1.4.1.3 "><p id="p13196202911427"><a name="p13196202911427"></a><a name="p13196202911427"></a>按钮主题为展示图标+标题。</p>
</td>
</tr>
<tr id="row21963296428"><td class="cellrowborder" valign="top" headers="mcps1.1.4.1.1 "><p id="p1519610297424"><a name="p1519610297424"></a><a name="p1519610297424"></a>HuaweiIdAuthButton.THEME_NO_TITLE</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.1.4.1.2 "><p id="p1419622944214"><a name="p1419622944214"></a><a name="p1419622944214"></a>按钮主题为不展示标题。</p>
</td>
</tr>
<tr id="row1519622994217"><td class="cellrowborder" rowspan="6" valign="top" width="30.403040304030405%" headers="mcps1.1.4.1.1 "><p id="p1919618296424"><a name="p1919618296424"></a><a name="p1919618296424"></a>setColorPolicy(int colorPolicy)</p>
</td>
<td class="cellrowborder" valign="top" width="36.26362636263626%" headers="mcps1.1.4.1.2 "><p id="p719616293423"><a name="p719616293423"></a><a name="p719616293423"></a>HuaweiIdAuthButton.COLOR_POLICY_BLUE</p>
</td>
<td class="cellrowborder" valign="top" width="33.33333333333333%" headers="mcps1.1.4.1.3 "><p id="p11963290424"><a name="p11963290424"></a><a name="p11963290424"></a>按钮颜色风格为蓝色，只有主题为THEME_FULL_TITLE时可用。</p>
</td>
</tr>
<tr id="row1219612974216"><td class="cellrowborder" valign="top" headers="mcps1.1.4.1.1 "><p id="p11962294424"><a name="p11962294424"></a><a name="p11962294424"></a>HuaweiIdAuthButton.COLOR_POLICY_BLACK</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.1.4.1.2 "><p id="p17196162904212"><a name="p17196162904212"></a><a name="p17196162904212"></a>按钮颜色风格为黑色。</p>
</td>
</tr>
<tr id="row11961429144216"><td class="cellrowborder" valign="top" headers="mcps1.1.4.1.1 "><p id="p619672916429"><a name="p619672916429"></a><a name="p619672916429"></a>HuaweiIdAuthButton.COLOR_POLICY_GRAY</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.1.4.1.2 "><p id="p18196929174210"><a name="p18196929174210"></a><a name="p18196929174210"></a>按钮颜色风格为灰色，只有主题为THEME_FULL_TITLE时可用。</p>
</td>
</tr>
<tr id="row17196102924212"><td class="cellrowborder" valign="top" headers="mcps1.1.4.1.1 "><p id="p61962292420"><a name="p61962292420"></a><a name="p61962292420"></a>HuaweiIdAuthButton.COLOR_POLICY_RED</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.1.4.1.2 "><p id="p619612917429"><a name="p619612917429"></a><a name="p619612917429"></a>按钮颜色风格为红色。</p>
</td>
</tr>
<tr id="row21961829174216"><td class="cellrowborder" valign="top" headers="mcps1.1.4.1.1 "><p id="p16197122910428"><a name="p16197122910428"></a><a name="p16197122910428"></a>HuaweiIdAuthButton.COLOR_POLICY_WHITE</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.1.4.1.2 "><p id="p17197112994211"><a name="p17197112994211"></a><a name="p17197112994211"></a>按钮颜色风格为白色。</p>
</td>
</tr>
<tr id="row16917165494415"><td class="cellrowborder" valign="top" headers="mcps1.1.4.1.1 "><p id="p189171054194415"><a name="p189171054194415"></a><a name="p189171054194415"></a>HuaweiIdAuthButton.COLOR_POLICY_WHITE_WITH_BORDER</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.1.4.1.2 "><p id="p179177542445"><a name="p179177542445"></a><a name="p179177542445"></a>按钮颜色风格为带描边白色，只有主题为THEME_FULL_TITLE时可用。</p>
</td>
</tr>
<tr id="row1025716286460"><td class="cellrowborder" rowspan="3" valign="top" width="30.403040304030405%" headers="mcps1.1.4.1.1 "><p id="p52401943154617"><a name="p52401943154617"></a><a name="p52401943154617"></a>setCornerRadius(int cornerRadiusPx)</p>
</td>
<td class="cellrowborder" valign="top" width="36.26362636263626%" headers="mcps1.1.4.1.2 "><p id="p325713288465"><a name="p325713288465"></a><a name="p325713288465"></a>HuaweiIdAuthButton.CORNER_RADIUS_LARGE</p>
</td>
<td class="cellrowborder" valign="top" width="33.33333333333333%" headers="mcps1.1.4.1.3 "><p id="p202571128204616"><a name="p202571128204616"></a><a name="p202571128204616"></a>按钮圆角设置，大圆角。</p>
</td>
</tr>
<tr id="row945722534619"><td class="cellrowborder" valign="top" headers="mcps1.1.4.1.1 "><p id="p732241544717"><a name="p732241544717"></a><a name="p732241544717"></a>HuaweiIdAuthButton.CORNER_RADIUS_MEDIUM</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.1.4.1.2 "><p id="p045762534610"><a name="p045762534610"></a><a name="p045762534610"></a>按钮圆角设置，中等圆角。</p>
</td>
</tr>
<tr id="row114751722164617"><td class="cellrowborder" valign="top" headers="mcps1.1.4.1.1 "><p id="p49046262477"><a name="p49046262477"></a><a name="p49046262477"></a>HuaweiIdAuthButton.CORNER_RADIUS_SMALL</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.1.4.1.2 "><p id="p18475192210460"><a name="p18475192210460"></a><a name="p18475192210460"></a>按钮圆角设置，小圆角。</p>
</td>
</tr>
<tr id="row08816317461"><td class="cellrowborder" valign="top" width="30.403040304030405%" headers="mcps1.1.4.1.1 "><p id="p178811031164611"><a name="p178811031164611"></a><a name="p178811031164611"></a>setUIMode(int theme, int colorPolicy, int cornerRadius)</p>
</td>
<td class="cellrowborder" valign="top" width="36.26362636263626%" headers="mcps1.1.4.1.2 "><p id="p1788103164611"><a name="p1788103164611"></a><a name="p1788103164611"></a>参考以上theme，colorPolicy，cornerRadius的可选值</p>
</td>
<td class="cellrowborder" valign="top" width="33.33333333333333%" headers="mcps1.1.4.1.3 "><p id="p388253124617"><a name="p388253124617"></a><a name="p388253124617"></a>设置HuaweiIdAuthButton的主题、颜色风格和圆角半径。</p>
</td>
</tr>
<tr id="row3241143511469"><td class="cellrowborder" valign="top" width="30.403040304030405%" headers="mcps1.1.4.1.1 "><p id="p324113510469"><a name="p324113510469"></a><a name="p324113510469"></a>setEnabled(boolean flag)</p>
</td>
<td class="cellrowborder" valign="top" width="36.26362636263626%" headers="mcps1.1.4.1.2 "><p id="p12419355466"><a name="p12419355466"></a><a name="p12419355466"></a>true/false</p>
</td>
<td class="cellrowborder" valign="top" width="33.33333333333333%" headers="mcps1.1.4.1.3 "><p id="p152411135124616"><a name="p152411135124616"></a><a name="p152411135124616"></a>设置是否可以点击。</p>
</td>
</tr>
</tbody>
</table>

**示例代码**

```
Java
HuaweiIdAuthButton huaweiIdAuthButton = new HuaweiIdAuthButton(this);
huaweiIdAuthButton.setOnClickListener(new View.OnClickListener() {
    @Override
    public void onClick(View v) {
        // 进行登录的操作处理
    }
});
huaweiIdAuthButton.setTheme(HuaweiIdAuthButton.THEME_FULL_TITLE);
huaweiIdAuthButton.setColorPolicy(HuaweiIdAuthButton.COLOR_POLICY_BLUE);
huaweiIdAuthButton.setCornerRadius(HuaweiIdAuthButton.CORNER_RADIUS_LARGE);
LinearLayout layout = findViewById(R.id.layout_sign_in_api);
layout.addView(huaweiIdAuthButton);
```

```
Kotlin
val huaweiIdAuthButton = HuaweiIdAuthButton(this)
huaweiIdAuthButton.setOnClickListener {
    // 进行登录的操作处理
}
huaweiIdAuthButton.theme = HuaweiIdAuthButton.THEME_FULL_TITLE
huaweiIdAuthButton.colorPolicy = HuaweiIdAuthButton.COLOR_POLICY_BLUE
huaweiIdAuthButton.cornerRadius = HuaweiIdAuthButton.CORNER_RADIUS_LARGE
val layout = findViewById<LinearLayout>(R.id.layout_sign_in_api)
layout.addView(huaweiIdAuthButton)
```

