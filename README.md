

1. 目标工程用 Unity 2022.3。先打开 **Window → TextMeshPro → Import TMP Essential Resources**。工程里还没有 TextMeshPro 时，先从 Package Manager 安装。
2. 菜单 **Assets → Import Package → Custom Package**，选 `PSD转UGUI.unitypackage`，全部导入。
3. 导入后出现 `Assets/PsdToUgui`。菜单是 **Tools → PSD转UGUI**。在 Project 里右键 PSD，也是这一项。
4. 生成的预制体和切图写到这个工程的 `Assets/PsdToUguiOutput`，不会改插件自带的示例。插件目录要留在工程里，色块用的白图在这里。
4. 生成的预制体和切图写到这个工程的 `Assets/PsdToUguiOutput`。插件目录要留在工程里，色块用的白图在这里。
## 先看示例
1. 在 Project 窗口选中 `Assets/PsdToUgui/Samples/Psd2UguiForm.psd`，右键 **PSD转UGUI**。会打开导入窗口并读入这个文件。
2. 也可以点 **Tools → PSD转UGUI**，在窗口里选这个文件。
3. 等 Console 出现「已生成」。预制体在 `Assets/PsdToUguiOutput/Psd2UguiForm/Psd2UguiForm.prefab`。
导入时会在当前场景放一份预览。场景里没有 Canvas 时，会自动加一个，参考分辨率用这份界面的 PSD 尺寸，并补上 EventSystem。
## 按钮、下拉框怎么点
按顶部的 **Play**，在 **Game** 视图里点。Scene 视图里点只会选中物体，按钮不会变色，下拉框也不会展开。
按钮按下会变深。没有挂自己的点击脚本，所以不会弹出别的界面。下拉框默认是收起的，点开才出现列表。滑动条的填充贴在轨道左侧，长度按 PSD 里填充和轨道的比例，按住轨道可以拖动。滚动列表要在运行后的 Game 视图里按住内容拖动；列表比窗口高时才会真正滚起来。
示例文件是 `Assets/PsdToUgui/Samples/Psd2UguiForm.psd`，尺寸 750×1334。里面有图片、文字、按钮、勾选、输入框、下拉框、滑动条和滚动列表。
## 导入自己的 PSD
1. 把 PSD 放进工程，在 Project 里选中它，右键 **PSD转UGUI**，会打开导入窗口。也可以点 **Tools → PSD转UGUI**，再用窗口里的「选择」指定文件。
2. 预制体写到 `Assets/PsdToUguiOutput/文件名/文件名.prefab`，切出来的图片在同目录的 `Sprites`。
3. 把预制体拖进场景里的 Canvas。根节点的宽高就是 PSD 的像素尺寸。
导入时会在当前场景放一份预览。场景里没有 Canvas 时，会自动加一个，参考分辨率用这份界面的 PSD 尺寸，并补上 EventSystem。
也可以点 **Tools → PSD转UGUI** 打开同一个窗口，标题是 **PSD转UGUI**。窗口右上角的 **使用说明** 会用系统默认的文本编辑器打开 `Assets/PsdToUgui/使用说明.md`。这次打开不带上次导入的 PSD，图层是空的，需要自己再选文件。在 Project 里右键生成出来的预制体，选 **PSD转UGUI**，窗口会按记录打开对应的 PSD。点左侧结构时，Hierarchy 里会选中对应物体；场景里没有这份界面时，会打开预制体再选中。窗口会留在主界面上面，点 Hierarchy、场景或 Inspector 时不会被关掉或盖住。窗口里选择 PSD 和导出目录。**生成 Layer** 决定物体落在哪个 Unity 层，默认是 UI。**界面资源** 填这一屏要引用的图片目录。**公共资源** 默认是 `Assets/PsdToUguiOutput/Shared`，一直参与查找，不用每次再加。同名图片先找界面资源，再找公共资源，找到就直接引用，不再导出新图。左侧是结构。点中一项时，Hierarchy 会同时选中场景里的物体。右侧信息里可以改名称、类型、零件、图片样式、引用和是否导出。图片样式可选普通、九宫格、平铺、填充。引用可选无、公共图、公共预制体；公共预制体目前只记在名称里，还不会嵌套预制体。位置、文字、颜色、锚点直接在 Inspector 里改。
点文字没有文本框，按画出来的像素框摆放，并且不自动换行。段落文字用 PSD 里的文本框当 Unity 的文字边框，只在这个框的宽度里换行。这样 PSD 里仍是一行的字，不会因为像素框太窄而被挤成两行。字号、颜色、段落的左右对齐按 PSD 读取。点文字默认上下左右居中。

