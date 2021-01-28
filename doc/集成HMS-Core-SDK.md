# 集成HMS Core SDK<a name="ZH-CN_TOPIC_0000001074016402"></a>

-   [添加当前应用的AppGallery Connect配置文件](#s252067eb744d4b208235a1790942f746)
-   [配置HMS Core SDK的Maven仓地址](#se8d2da53983045f8b5e495e4f8681cc5)
-   [添加编译依赖](#s98126f944ea44f2d9aed2431b3330eda)
-   [多语言设置](#sa72621e6753f4f8eb55dc32d38e65acb)
-   [同步工程](#s52e4ed6bb7c643cba2141d020b795213)
-   [配置元数据](#section6979644205018)
-   [配置AndroidManifest.xml文件](#section184051734228)

针对Android Studio开发环境，华为提供了Maven仓集成方式的HMS Core SDK包。在开始开发前，您需要将HMS Core SDK集成到您的Android Studio开发环境中。

## 添加当前应用的AppGallery Connect配置文件<a name="s252067eb744d4b208235a1790942f746"></a>

如果在AppGallery Connect中开通了相关服务则需要将“agconnect-services.json“文件添加到您的App中。

1.  登录[AppGallery Connect](https://developer.huawei.com/consumer/cn/service/josp/agc/index.html)网站，点击“我的项目“。
2.  在项目列表中找到您的项目，在项目中点击需要集成HMS Core SDK的应用。
3.  在“项目设置  \>  常规“页面的“应用“区域，点击“agconnect-services.json“下载配置文件。

    ![](figures/2.png)

4.  将“agconnect-services.json“文件拷贝到应用级根目录下。

    ![](figures/3.png)


## 配置HMS Core SDK的Maven仓地址<a name="se8d2da53983045f8b5e495e4f8681cc5"></a>

1.  打开Android Studio项目级“build.gradle“文件。

    ![](figures/4.png)

2.  添加HUAWEI agcp插件以及Maven代码库。

    -   在“buildscript  \>  repositories“中配置HMS Core SDK的Maven仓地址。
    -   在“allprojects  \>  repositories“中配置HMS Core SDK的Maven仓地址。
    -   如果App中添加了“agconnect-services.json“文件则需要在“buildscript  \>  dependencies“中增加agcp配置。

        ```
        buildscript {
            repositories {
                google()
                jcenter()
                // 配置HMS Core SDK的Maven仓地址。
                maven {url 'https://developer.huawei.com/repo/'}
            }
            dependencies {
                ...
                // 增加agcp配置。
                classpath 'com.huawei.agconnect:agcp:1.4.2.300'
            }
        }
        
        allprojects {
            repositories {
                google()
                jcenter()
                // 配置HMS Core SDK的Maven仓地址。
                maven {url 'https://developer.huawei.com/repo/'}
            }
        } 
        ```


    >![](public_sys-resources/icon-note.gif) **说明：** 
    >Maven仓地址无法直接在浏览器中打开访问，只能在IDE中配置。如需添加多个Maven代码库，请将华为公司的Maven仓地址配置在最后。


## 添加编译依赖<a name="s98126f944ea44f2d9aed2431b3330eda"></a>

1.  打开应用级的“build.gradle“文件。

    ![](figures/6.png)

2.  在“dependencies“中添加如下编译依赖。

    ```
    dependencies {
        implementation 'com.huawei.hms:hwid:{version}'
    }
    ```

    >![](public_sys-resources/icon-note.gif) **说明：** 
    >hwid为华为帐号服务，_\{version\}_替换为实际的SDK版本号，版本号索引请参见[版本更新说明](版本更新说明.md)。例如：implementation 'com.huawei.hms:**hwid:5.1.0.301**'。

3.  在文件头**apply plugin: 'com.android.application'**下一行添加如下配置。

    ```
    apply plugin: 'com.huawei.agconnect'
    ```


## 多语言设置<a name="sa72621e6753f4f8eb55dc32d38e65acb"></a>

-   如果您的应用不需要设置只支持某些特定语言，则请忽略本步骤。应用将默认支持所有HMS Core SDK支持的语言。
-   如果您的应用需要设置只支持某些特定语言，则可通过本步骤配置。

    1.  打开应用级的“build.gradle“文件。

        ![](figures/6-0.png)


    1.  在“android  \>  defaultConfig“中新增“resConfigs“，配置需要支持的语种，配置格式如下：

        ```
        android {
                defaultConfig {
                        ...
                        resConfigs "en", "zh-rCN", "需要支持的其他语言"
                }
        }        
        ```


    HMS Core SDK支持的语言列表请参见[HMS Core SDK支持的语言](zh-cn_topic_0000001050040564.md)。


## 同步工程<a name="s52e4ed6bb7c643cba2141d020b795213"></a>

在完成以上的配置后，点击工具栏中的gradle同步图标，完成“build.gradle“文件的同步，将相关依赖下载到本地。

![](figures/zh-cn_image_0000001073788327.png)

>![](public_sys-resources/icon-note.gif) **说明：** 
>如果出现错误，请检查网络连接是否正常，以及检查“build.gradle“文件是否正确。

## 配置元数据<a name="section6979644205018"></a>

-   如果您的应用上架到Google Play：当用户手机上未安装HMS Core（APK）或者版本过低时，使用应用会返回错误，但不会引导用户安装或升级HMS Core（APK）。
-   如果您的应用不上架到Google Play：进行如下配置，当用户手机上未安装HMS Core（APK）或者版本过低时，引导用户安装或升级HMS Core（APK）。
    1.  在“AndroidManifest.xml“的Application中增加以下元数据。

        ```
        <application ...>
            <meta-data     
               android:name="com.huawei.hms.client.channel.androidMarket"  
               android:value="false" />
            ...
        </application>
        ```

    2.  添加升级解决方案。
        -   如果您是通过Activity调用API，HMS Core SDK会自动安装或升级HMS Core（APK），无需特别处理。
        -   如果您是通过Context调用API，在接口返回的[Task](zh-cn_topic_0000001050121148.md)回调中添加如下解决方案，实现安装或升级HMS Core（APK）。

            ```
            task.addOnFailureListener(new OnFailureListener() {
                @Override
                public void onFailure(Exception e) {
                    // 当收到的异常为ResolvableApiException实例时，说明这时需要引导安装或升级HMS Core（APK）。
                    if (e instanceof ResolvableApiException) {
                        ResolvableApiException apiException = (ResolvableApiException)e;
                        // 调用apiException中的pendingIntent，传入requestCode参数。
                        try {
                            apiException.startResolutionForResult(MainActivity.this, requestCode);
                        } catch (IntentSender.SendIntentException ex) {
                            ex.printStackTrace();
                        }
                    }
                }
            });
            ```




## 配置AndroidManifest.xml文件<a name="section184051734228"></a>

Android 11更改了应用查询用户在设备上已安装的其他应用以及与之交互的方式。使用<queries\>元素，可以为应用定义一组自身可访问的其他应用。

如果targetSdkVersion是30或者更高版本，您需要在“AndroidManifest.xml“中manifest便签下添加<queries\>元素，使应用可以访问HMS Core（APK）。

```
<manifest ...>
    ...
    <queries>
        <intent>
            <action android:name="com.huawei.hms.core.aidlservice" />
        </intent>
    </queries>
    ...
</manifest>
```

>![](public_sys-resources/icon-note.gif) **说明：** 
><queries\>元素对工具的要求如下：
>-   Android Studio 3.3或更高版本。
>-   Android Studio版本支持的[Android Gradle插件](https://developer.android.com/studio/releases/gradle-plugin)最新“点”版本。点击[了解详情](https://android-developers.googleblog.com/2020/07/preparing-your-build-for-package-visibility-in-android-11.html)。

