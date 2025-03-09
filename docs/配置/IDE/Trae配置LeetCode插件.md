# Trae配置LeetCode插件

在 vsCode 和 IDEA 上配置 LeetCode 插件比较常见及简单，掌握这个方法可以融会贯通；

由于Trae目前在插件市场暂不支持直接下载LeetCode插件，我们需要手动对力扣插件进行导入，Trae管理插件文档如下：

[管理插件](https://docs.trae.ai/docs/manage-extensions)

### 从 vscode 插件市场下载 LeetCode 插件

[力扣插件](https://marketplace.visualstudio.com/items?itemName=LeetCode.vscode-leetcode)

![](images/mk-2025-03-10-00-48-11.png ':size=100%')

在这个页面中点击 **Version History**，选择合适的version，并从页面URL中记录fieldA和fieldB字段的值，这两个字段是键itemName的值，小数点前为fieldA，小数点后为fieldB。例如：

![](images/mk-2025-03-10-00-51-03.png ':size=100%')

上图的fieldA为：LeetCode，fieldB为：vscode-leetcode；

接下来将上方提取到的fieldA、fieldB和version字段按照下述模板进行填充并访问，即可下载该插件的vsix文件：

```
https://marketplace.visualstudio.com/_apis/public/gallery/publishers/${itemName.fieldA}/vsextensions/${itemName.fieldB}/${version}/vspackage
```

将下载的vsix文件拖拽至Trae插件市场面板后即可自动安装；

下方给出一个配置好的URL，可直接使用：

```
https://marketplace.visualstudio.com/_apis/public/gallery/publishers/%E5%8A%9B%E6%89%A3%20LeetCode/vsextensions/LeetCode.vscode-leetcode/0.18.4/vspackage
```

### 插件配置

**登录**

使用Trae登录力扣插件时需要注意，不要使用Web Authorization方式，使用这种方式会自动跳转vscode进行插件下载；

如果想要使用Trae力扣插件的话，要选择LeetCode Cookie登录方式，登录网页版力扣之后，F12打开控制台，输入document.cookie，将获取到的cookie值复制到Trae中即可；

**配置**
- Allow Report Data：取消勾选，该选项是发送数据给力扣，没有必要开启；
- Default Language：默认语言；
- Endpoint：后缀有cn的是力扣中国区；
- Node Path：需要配置本地Node.exe的路径；
- Workspace Floder：代码保存位置；