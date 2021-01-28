# 配置AppGallery Connect<a name="ZH-CN_TOPIC_0000001074654194"></a>

-   [注册成为开发者](#sd973d2b3babc4a53b9709da2f0a6de5a)
-   [创建应用](#sf8652dd31d3844bb846cd7a73ce9db99)
-   [生成签名证书指纹](#s07af9eb630b94aab8dc2fe350a40b782)
-   [配置签名证书指纹](#s7f738615920f4b22bf0dabcdbb3839ea)

在开发应用前，需要在AppGallery Connect中配置相关信息。

## 注册成为开发者<a name="sd973d2b3babc4a53b9709da2f0a6de5a"></a>

在开发应用前需要在[华为开发者联盟](https://developer.huawei.com/consumer/cn)网站上注册成为开发者并完成实名认证，具体方法请参见[帐号注册认证](https://developer.huawei.com/consumer/cn/doc/start/registration-and-verification-0000001053628148)。

## 创建应用<a name="sf8652dd31d3844bb846cd7a73ce9db99"></a>

参见[创建项目](https://developer.huawei.com/consumer/cn/doc/development/AppGallery-connect-Guides/agc-get-started#createproject)和[在项目下添加应用](https://developer.huawei.com/consumer/cn/doc/development/AppGallery-connect-Guides/agc-get-started#createapp)完成应用的创建。

## 生成签名证书指纹<a name="s07af9eb630b94aab8dc2fe350a40b782"></a>

签名证书指纹用于校验应用的真实性，您需要根据签名证书在本地生成签名证书指纹，并在应用上架前将签名证书指纹配置到AppGallery Connect。

在申请前需要满足以下两个条件：

-   已创建应用程序的签名证书，签名证书创建请参见[生成签名证书](https://developer.huawei.com/consumer/cn/codelab/HMSPreparation/index.html#2)。
-   当前PC已经安装[JDK](https://www.oracle.com/java/technologies/javase-downloads.html)。

操作步骤如下：

-   Windows
    1.  使用CMD命令打开命令行工具，执行**cd**命令进入keytool.exe所在的目录（以下样例为JDK安装在C盘的Program Files目录）。

        ```
        C:\>cd C:\Program Files\Java\jdk\bin
        ```

    2.  执行命令**keytool -list -v -keystore **_<keystore-file\>_，按命令行提示进行操作。<keystore-file\>为应用签名文件的完整路径。

        例如：

        ```
        keytool -list -v -keystore C:\TestApp.jks
        ```

    3.  根据结果获取对应的SHA256指纹。

        ![](figures/1-(3).png)


-   macOS
    1.  打开Terminal终端。

        ![](figures/1ec456aba1a5b096.png)

    2.  执行命令**keytool -list -v -keystore **_<keystore-file\>_，按命令行提示进行操作。<keystore-file\>为应用签名文件的完整路径。

        例如：

        ```
        keytool -list -v -keystore /Users/admin/Downloads/HmsDemo.jks
        ```

    3.  根据结果获取对应的SHA256指纹。

        ![](figures/f2ce1c48c3d12713.png)



## 配置签名证书指纹<a name="s7f738615920f4b22bf0dabcdbb3839ea"></a>

1.  登录[AppGallery Connect](https://developer.huawei.com/consumer/cn/service/josp/agc/index.html)网站，点击“我的项目“。
2.  在项目列表中找到您的项目，在项目中点击需要配置签名证书指纹的应用。
3.  在“项目设置  \>  常规“页面的“应用“区域，点击“SHA256证书指纹“后的![](figures/zh-cn_image_0000001073976437.png)图标，输入生成的SHA256指纹。

    ![](figures/unnaming-(5).png)

4.  配置完成后点击![](figures/zh-cn_image_0000001074494270.png)。

