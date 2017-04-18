---
title: "如何：创建项模板 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project item templates, XML reference
- project item templates, custom template locations
- project item templates, creating
- project item templates, metadata files
ms.assetid: 77bc53d4-d607-4820-a032-7e3b365891b5
caps.latest.revision: 23
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 9b29250916c91c98176585bbdb8c5a4018dbd6c7
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-create-item-templates"></a>如何：创建项模板
本主题[第一个过程](../ide/how-to-create-item-templates.md#export_template)中的步骤演示如何使用“导出模板”向导创建项模板。 如果模板将由多个文件组成，请参阅[如何：创建多文件项模板](../ide/how-to-create-multi-file-item-templates.md)。  

 向导执行大量工作为你创建基本模板，但在许多情况下，你将需要在导出模板后手动修改 .vstemplate 文件。 例如，如果希望该项显示在 [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] 应用项目的“添加新项”对话框中，则需要执行一些额外步骤。 本主题中的[第二个过程](../ide/how-to-create-item-templates.md#modify_template)有助于完成该任务。  

 若要指定应仅对某些项目子类型（如 Office、数据库或 Web）显示模板，请参阅[本节](../ide/how-to-create-multi-file-item-templates.md#enable_templates)。  

 在某些情况下，你可能希望或需要从头开始手动创建项模板。 [第三个过程](../ide/how-to-create-item-templates.md#create_template)演示如何做到这一点。  

 若要了解可以在 .vstemplate 文件中使用的元素，请参阅 [Visual Studio 模板架构引用](../extensibility/visual-studio-template-schema-reference.md)。  

### <a name="to-add-a-custom-project-item-template-to-the-add-new-item-dialog-box"></a>将自定义项目项模板添加到“添加新项”对话框中  

1.  在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中创建或打开一个项目。  

2.  向项目添加一项，并在需要时修改它。  

3.  修改代码文件，以指示应进行参数替换的位置。 有关详细信息，请参阅[如何：替换模板中的参数](../ide/how-to-substitute-parameters-in-a-template.md)。  

4.  在“文件”菜单上，单击“导出模板”。  

5.  单击“项模板”，选择包含该项的项目，然后单击“下一步”。  

6.  选择要为其创建模板的项，然后单击“下一步”。  

7.  选择要包含到模板中的程序集引用，然后单击“下一步”。  

8.  键入图标文件名、预览图像、模板名称和模板说明，然后单击“完成”。  

     模板文件被添加到 .zip 文件中，并复制到你在对话框中指定的任何目录。 默认位置是 **..\Users\\<username\>\Documents\Visual Studio \<Version>\My Exported Templates\\** 文件夹。  

    > [!WARNING]
    >  在 Visual Studio 的早期版本中，默认位置是 **..\Users\\<username\>\Documents\Visual Studio \<Version>\Templates\ItemTemplates**。  

### <a name="to-enable-the-item-template-to-be-used-in-a-store-project"></a>启用要在应用商店项目中使用的项模板  

1.  按照上述过程中的步骤导出项目模板。  

2.  从复制到 ..\Users\\username\Documents\Visual Studio Version\Templates\ItemTemplates\（或 **My Exported Templates**）文件夹的 .zip 文件中提取 .vstemplate 文件。  

3.  在 Visual Studio 中打开 .vstemplate 文件。  

4.  对于 Windows 8.1 应用商店 C# 项目，在 .vstemplate 文件的开始和结束 `<TemplateData>` 标记内添加以下 XML：`<TemplateGroupID>WinRT-Managed</TemplateGroupID>`。  

     C++ Windows 8.1 应用商店项目使用的值为 `WinRT-Native-6.3`。 有关 Windows 10 及其他项目类型，请参阅 [TemplateGroupID 元素（Visual Studio 模板）](../extensibility/templategroupid-element-visual-studio-templates.md)。  

     下面的示例显示添加 XML 行 `<TemplateGroupID>WinRT-Managed</TemplateGroupID>` 之后，.vstemplate 文件的全部内容。 此示例特定于 C# 项目。 可以修改 <ProjectTpe> 和 \<[TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md)> 元素，从而指定其他语言和项目类型。  

    ```xml  
    <VSTemplate Version="3.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Item">  
      <TemplateData>  
        <DefaultName>MyItemStoreTemplate.xaml</DefaultName>  
        <Name>MyItemStoreTemplate</Name>  
        <Description>This is an example itemtemplate</Description>  
        <ProjectType>CSharp</ProjectType>  
        <SortOrder>10</SortOrder>  
        <Icon>__TemplateIcon.ico</Icon>  
        <TemplateGroupID>WinRT-Managed</TemplateGroupID>  
      </TemplateData>  
      <TemplateContent>  
        <References />  
        <ProjectItem SubType="Designer" TargetFileName="$fileinputname$.xaml" ReplaceParameters="true">MyItemTemplate.xaml</ProjectItem>  
        <ProjectItem SubType="Code" TargetFileName="$fileinputname$.xaml.cs" ReplaceParameters="true">MyItemTemplate.xaml.cs</ProjectItem>  
      </TemplateContent>  
    </VSTemplate>  
    ```  

     有关其他可能的 TemplateGroupID 值，请参阅 [TemplateGroupID 元素（Visual Studio 模板）](../extensibility/templategroupid-element-visual-studio-templates.md)。 有关完整的 .vstemplate 引用，请参阅 [Visual Studio 模板架构引用](../extensibility/visual-studio-template-schema-reference.md)  

5.  在 Visual Studio 中，保存 .vstemplate 文件并将其关闭。  

6.  复制 .vstemplate 文件并将其粘贴至 ..\Users\\username\Documents\Visual Studio Version\Templates\ItemTemplates\ 文件夹中的 .zip 文件。  

     如果出现“复制文件”对话框，请选择“复制和替换”选项。  

 现在，可以使用“添加新项”对话框，将基于此模板的项添加到 [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] 项目。  

 有关参数名称的详细信息，请参阅[模板参数](../ide/template-parameters.md)。  

### <a name="to-enable-templates-for-specific-project-sub-types"></a>启用特定项目子类型的模板  

1.  借助开发环境，你可以将项目项设置为在某些项目的“添加项”对话框中可用。 请遵循此过程以使自定义项可用于 Windows、Web、Office 或数据库项目。  

     在项模板的 .vstemplate 文件中找到 ProjectType 元素。  

     在 ProjectType 元素之后添加一个 [ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md) 元素。  

2.  将该元素的文本值设置为下列值之一：  

    1.  Windows  

    2.  Office  

    3.  数据库  

    4.  Web  

     例如：`<ProjectSubType>Database</ProjectSubType>`。  

     下面的示例演示可用于 Office 项目的项模板。  

    ```  
    <VSTemplate Version="2.0.0" Type="Item" Version="2.0.0">  
        <TemplateData>  
            <Name>Class</Name>  
            <Description>An empty class file</Description>  
            <Icon>Class.ico</Icon>  
            <ProjectType>CSharp</ProjectType>  
            <ProjectSubType>Office</ProjectSubType>  
            <DefaultName>Class.cs</DefaultName>  
        </TemplateData>  
        <TemplateContent>  
            <ProjectItem>Class1.cs</ProjectItem>  
        </TemplateContent>  
    </VSTemplate>  

    ```  

### <a name="to-manually-create-an-item-template-without-using-the-export-template-wizard"></a>在不使用“导出模板”向导的情况下手动创建项模板  

1.  创建项目和项目项。  

2.  修改项目项，直到可以将它另存为一个模板。  

3.  根据需要，修改代码文件以指示应进行参数替换的位置。 有关参数替换的详细信息，请参阅“如何：替换模板中的参数”。  

4.  创建一个 XML 文件，并使用 .vstemplate 文件扩展名将其保存到与新项模板相同的目录中。  

5.  创建 .vstemplate XML 文件以提供项模板元数据。 有关详细信息，请参阅 [Visual Studio 模板架构引用](../extensibility/visual-studio-template-schema-reference.md)以及上一节中的示例。  

6.  保存 .vstemplate 文件并将其关闭。  

7.  在 Windows 资源管理器中，选择要包括到模板中的文件，右键单击所选内容，单击“发送到”，然后单击“压缩(zipped)文件夹”。 所选的文件被压缩到一个 .zip 文件中。  

8.  复制该 .zip 文件并将其粘贴到用户的项模板位置。 在 Visual Studio 2017 中，默认目录是..\Users\\<username\>\Documents\Visual Studio 2017\Templates\ItemTemplates\\。 有关详细信息，请参阅“如何：查找和组织项目和项模板”。  

## <a name="see-also"></a>另请参阅  
 [创建项目和项模板](../ide/creating-project-and-item-templates.md)   
 [如何：创建多文件项模板](../ide/how-to-create-multi-file-item-templates.md)   
 [Visual Studio 模板架构参考](../extensibility/visual-studio-template-schema-reference.md)
