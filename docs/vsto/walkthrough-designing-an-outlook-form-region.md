---
title: "演练：设计 Outlook 窗体区域"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "窗体区域 [Visual Studio 中的 Office 开发], 创建"
ms.assetid: b033fc06-cdeb-4d7f-804b-86d15bfa022a
caps.latest.revision: 41
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 40
---
# 演练：设计 Outlook 窗体区域
  自定义窗体区域扩展标准或自定义 Microsoft Office Outlook 窗体。  在本演练中，你将设计作为新页出现在联系人项目的检查器窗口中的自定义窗体区域。  通过将地址信息发送到 Windows Live 本地搜索网站，此窗体区域将显示为联系人列出的每个地址的映射。  有关窗体区域的信息，请参阅[创建 Outlook 窗体区域](../vsto/creating-outlook-form-regions.md)。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 本演练阐释了以下任务：  
  
-   创建新的 Outlook VSTO 外接程序项目。  
  
-   将窗体区域添加到 VSTO 外接程序项目。  
  
-   设计窗体区域的布局。  
  
-   自定义窗体区域的行为。  
  
-   测试 Outlook 窗体区域。  
  
> [!NOTE]  
>  以下说明中的某些 Visual Studio 用户界面元素在计算机上出现的名称或位置可能会不同。  这些元素取决于你所使用的 Visual Studio 版本和你所使用的设置。  有关详细信息，请参阅 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-cn/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
## 系统必备  
 你需要以下组件来完成本演练：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Outlook_15_short](../vsto/includes/outlook-15-short-md.md)] 或 [!INCLUDE[Outlook_14_short](../vsto/includes/outlook-14-short-md.md)]。  
  
 ![链接到视频](~/data-tools/media/playvideo.gif "链接到视频") 有关本主题的视频版本，请参阅[视频帮助：设计 Outlook 窗体区域](http://go.microsoft.com/fwlink/?LinkID=140824)。  
  
## 创建新的 Outlook VSTO 外接程序项目  
 首先创建基本的 VSTO 外接程序项目。  
  
#### 创建新的 Outlook VSTO 外接程序项目  
  
1.  在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中，创建名为 MapItAddIn 的 VSTO 外接程序项目。  
  
2.  在**“新建项目”**对话框中，选择**“创建解决方案的目录”**。  
  
3.  将项目保存到任一目录。  
  
     有关详细信息，请参阅[如何：在 Visual Studio 中创建 Office 项目](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
## 向 Outlook VSTO 外接程序项目添加窗体区域  
 Outlook VSTO 外接程序解决方案可包含一个或多个 Outlook 窗体区域项。  使用**“新建 Outlook 窗体区域”**向导将窗体区域项添加到项目中。  
  
#### 向 Outlook VSTO 外接程序项目添加窗体区域  
  
1.  在**“解决方案资源管理器”**中，选择**“MapItAddIn”**项目。  
  
2.  在**“项目”**菜单上，单击**“添加新项”**。  
  
3.  在**“添加新项”**对话框中，选择**“Outlook 窗体区域”**，将文件命名为 MapIt，然后单击**“添加”**。  
  
     将**“新建Outlook 窗体区域”**向导启动。  
  
4.  在**“选择窗体区域的创建方式”**页上，单击**“设计新的窗体区域”**，然后单击**“下一步”**。  
  
5.  在**“选择要创建的窗体区域的类型”**页上，单击**“独立”**，然后单击**“下一步”**。  
  
     *“独立”*窗体区域将向 Outlook 窗体添加新页。  有关窗体区域类型的详细信息，请参阅[创建 Outlook 窗体区域](../vsto/creating-outlook-form-regions.md)。  
  
6.  在**“提供说明性文本并选择显示首选项”**页上，在**“名称”**框中键入 **Map It**。  
  
     打开联系人项目时，此名称将显示在检查器窗口的功能区中。  
  
7.  选择**“撰写模式下的检查器”**和**“读取模式下的检查器”**，然后单击**“下一步”**。  
  
8.  在**“标识将显示此窗体区域的邮件类”**页上，清除**“邮件”**，选择**“联系人”**，然后单击**“完成”**。  
  
     MapIt.cs 或 MapIt.vb 文件将添加到项目中。  
  
## 设计窗体区域的布局  
 使用*窗体区域设计器*直观地开发窗体区域。  可将托管的控件拖到窗体区域设计器图面。  使用设计器和**“属性”**窗口来调整控件的布局和外观。  
  
#### 设计窗体区域的布局  
  
1.  在**“解决方案资源管理器”**中，展开**“MapItAddIn”**项目，然后双击 MapIt.cs 或 MapIt.vb 以打开窗体区域设计器。  
  
2.  右键单击设计器，然后单击**“属性”**。  
  
3.  在**“属性”**窗口中，将**“大小”**设置为 664、469。  
  
     这可确保窗体区域的大小足以显示映射。  
  
4.  在**“视图”**菜单上单击**“工具箱”**。  
  
5.  在**“工具箱”**的**“公共控件”**选项卡中，将**“WebBrowser”**添加到窗体区域。  
  
     **“WebBrowser”**将显示为联系人列出的每个地址的映射。  
  
## 自定义窗体区域的行为  
 将代码添加到窗体区域事件处理程序，从而自定义窗体区域在运行时的行为方式。  对于此窗体区域而言，代码将检查 Outlook 项的属性，并确定是否显示 Map It 窗体区域。  如果它显示该窗体区域，代码将导航到 Windows Live 本地搜索并加载 Outlook 联系人项目中列出的每个地址的映射。  
  
#### 自定义窗体区域的行为  
  
1.  在**“解决方案资源管理器”**中，右键单击“MapIt.cs”或“MapIt.vb”，然后单击**“查看代码”**。  
  
     MapIt.cs 或 MapIt.vb 将在代码编辑器中打开。  
  
2.  展开**“窗体区域工厂”**代码区域。  
  
     将公开名为 `MapItFactory` 的窗体区域工厂类。  
  
3.  将以下代码添加到 `MapItFactory_FormRegionInitializing` 事件处理程序中。  将在用户打开联系人项目时调用此事件处理程序。  下面的代码确定联系人项目是否包含地址。  如果联系人项目不包含地址，则此代码将 <xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs> 类的 <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> 属性设置为 **true**，并且不显示窗体区域。  否则，VSTO 外接程序将引发 <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing> 事件，并显示窗体区域。  
  
     [!code-csharp[Trin_Outlook_FR_Separate#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Outlook_FR_Separate/CS/MapIt.cs#1)]
     [!code-vb[Trin_Outlook_FR_Separate#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Outlook_FR_Separate/VB/MapIt.vb#1)]  
  
4.  将以下代码添加到 <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing> 事件处理程序中。  这段代码执行下列任务：  
  
    -   将联系人项目中的每个地址连接起来，并创建一个 URL 字符串。  
  
    -   调用 <xref:System.Windows.Forms.WebBrowser> 对象的 <xref:System.Windows.Forms.WebBrowser.Navigate%2A> 方法，并将 URL 字符串作为参数传递。  
  
     本地搜索网站将在 Map It 窗体区域中出现，并在便笺本中显示每个地址。  
  
     [!code-csharp[Trin_Outlook_FR_Separate#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Outlook_FR_Separate/CS/MapIt.cs#2)]
     [!code-vb[Trin_Outlook_FR_Separate#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Outlook_FR_Separate/VB/MapIt.vb#2)]  
  
## 测试 Outlook 窗体区域  
 运行项目时，Visual Studio 将打开 Outlook。  打开联系人项目以查看 Map It 窗体区域。  Map It 窗体区域显示为包含地址的任何联系人项目的窗体中的页面。  
  
#### 测试 Map It 窗体区域  
  
1.  按 F5 运行项目。  
  
     Outlook 将打开。  
  
2.  在 Outlook 中，在**“主页”**选项卡上，单击**“新建项”**，然后单击**“联系人”**。  
  
3.  在联系人窗体中，键入 **Ann Beebe** 作为联系人姓名，然后指定以下三个地址。  
  
    |地址类型|地址|  
    |----------|--------|  
    |**业务**|4567 Main St.  Buffalo, NY|  
    |**主页**|1234 North St.  Buffalo, NY|  
    |**其他**|3456 Main St.  Seattle, WA|  
  
4.  保存并关闭联系人项目。  
  
5.  重新打开**“Ann Beebe”**联系人项目。  
  
6.  在项功能区的**“显示”**组中，单击**“Map It”**以打开 Map It 窗体区域。  
  
     Map It 窗体区域出现，并显示本地搜索网站。  **“业务”**、**“主页”**和**“其他”**地址将出现在便笺本中。  在便笺本中，选择需映射的地址。  
  
## 后续步骤  
 可从以下主题了解有关如何自定义 Outlook 应用程序 UI 的详细信息：  
  
-   若要了解如何自定义 Outlook 项的功能区，请参阅[自定义 Outlook 功能区](../vsto/customizing-a-ribbon-for-outlook.md)。  
  
## 请参阅  
 [在运行时访问窗体区域](../vsto/accessing-a-form-region-at-run-time.md)   
 [创建 Outlook 窗体区域](../vsto/creating-outlook-form-regions.md)   
 [Outlook 窗体区域创建准则](../vsto/guidelines-for-creating-outlook-form-regions.md)   
 [演练：导入在 Outlook 中设计的窗体区域](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)   
 [如何：向 Outlook 外接程序项目中添加窗体区域](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)   
 [将窗体区域与 Outlook 邮件类关联](../vsto/associating-a-form-region-with-an-outlook-message-class.md)   
 [Outlook 窗体区域中的自定义操作](../vsto/custom-actions-in-outlook-form-regions.md)   
 [如何：防止 Outlook 显示窗体区域](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)  
  
  