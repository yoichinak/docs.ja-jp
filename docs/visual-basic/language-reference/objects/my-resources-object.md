---
title: My.Resources オブジェクト
ms.date: 07/20/2015
f1_keywords:
- My.Resources
- My.Resources.MyResources.ResourceManager
- My.Resources.MyResources.Culture
helpviewer_keywords:
- My.Resources object
ms.assetid: 34c3f2dc-7b87-432c-9d5f-17ea666bb266
ms.openlocfilehash: 7f5d81194123ad2151a494a3cb79aa1955e0fdad
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350327"
---
# <a name="myresources-object"></a>My.Resources オブジェクト
Provides properties and classes for accessing the application's resources.  
  
## <a name="remarks"></a>Remarks  
 The `My.Resources` object provides access to the application's resources and lets you dynamically retrieve resources for your application. For more information, see [Managing Application Resources (.NET)](/visualstudio/ide/managing-application-resources-dotnet).  
  
 The `My.Resources` object exposes only global resources. It does not provide access to resource files associated with forms. You must access the form resources from the form.  
  
 You can access the application's culture-specific resource files from the `My.Resources` object. By default, the `My.Resources` object looks up resources from the resource file that matches the culture in the <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.UICulture%2A> property. However, you can override this behavior and specify a particular culture to use for the resources. 詳細については、「[デスクトップ アプリケーションのリソース](../../../framework/resources/index.md)」を参照してください。  
  
## <a name="properties"></a>プロパティ  
 The properties of the `My.Resources` object provide read-only access to your application's resources. To add or remove resources, use the **Project Designer**. You can access resources added through the **Project Designer** by using `My.Resources.`*resourceName*.  
  
 You can also add or remove resource files by selecting your project in **Solution Explorer** and clicking **Add New Item** or **Add Existing Item** from the **Project** menu. You can access resources added in this manner by using `My.Resources.`*resourceFileName*`.`*resourceName*.  
  
 Each resource has a name, category, and value, and these resource settings determine how the property to access the resource appears in the `My.Resources` object. For resources added in the **Project Designer**:  
  
- The name determines the name of the property,  
  
- The resource data is the value of the property,  
  
- The category determines the type of the property:  
  
|カテゴリ|Property data type|  
|---|---|  
|**文字列**|[String](../../../visual-basic/language-reference/data-types/string-data-type.md)|  
|**イメージ**|<xref:System.Drawing.Bitmap>|  
|**アイコン**|<xref:System.Drawing.Icon>|  
|**オーディオ**|<xref:System.IO.UnmanagedMemoryStream><br /><br /> The <xref:System.IO.UnmanagedMemoryStream> class derives from the <xref:System.IO.Stream> class, so it can be used with methods that take streams, such as the <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A> method.|  
|**ファイル**|-   [String](../../../visual-basic/language-reference/data-types/string-data-type.md) for text files.<br />-   <xref:System.Drawing.Bitmap> for image files.<br />-   <xref:System.Drawing.Icon> for icon files.<br />-   <xref:System.IO.UnmanagedMemoryStream> for sound files.|  
|**その他**|Determined by the information in the designer's **Type** column.|  
  
## <a name="classes"></a>クラス  
 The `My.Resources` object exposes each resource file as a class with shared properties. The class name is the same as the name of the resource file. As described in the previous section, the resources in a resource file are exposed as properties in the class.  
  
## <a name="example"></a>例  
 This example sets the title of a form to the string resource named `Form1Title` in the application resource file. For the example to work, the application must have a string named `Form1Title` in its resource file.  
  
 [!code-vb[VbVbalrMyResources#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#1)]  
  
## <a name="example"></a>例  
 This example sets the icon of the form to the icon named `Form1Icon` that is stored in the application's resource file. For the example to work, the application must have an icon named `Form1Icon` in its resource file.  
  
 [!code-vb[VbVbalrMyResources#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#2)]  
  
## <a name="example"></a>例  
 This example sets the background image of a form to the image resource named `Form1Background`, which is in the application resource file. For this example to work, the application must have an image resource named `Form1Background` in its resource file.  
  
 [!code-vb[VbVbalrMyResources#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#3)]  
  
## <a name="example"></a>例  
 This example plays the sound that is stored as an audio resource named `Form1Greeting` in the application's resource file. For the example to work, the application must have an audio resource named `Form1Greeting` in its resource file. The `My.Computer.Audio.Play` method is available only for Windows Forms applications.  
  
 [!code-vb[VbVbalrMyResources#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#4)]  
  
## <a name="example"></a>例  
 This example retrieves the French-culture version of a  string resource of the application. The resource is named `Message`. To change the culture that the `My.Resources` object uses, the example uses <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.ChangeUICulture%2A>.  
  
 For this example to work, the application must have a string named `Message` in its resource file, and the application should have the French-culture version of that resource file, Resources.fr-FR.resx. If the application does not have the French-culture version of the resource file, the `My.Resource` object retrieves the resource from the default-culture resource file.  
  
 [!code-vb[VbVbalrMyResources#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#10)]  
  
## <a name="see-also"></a>関連項目

- [アプリケーション リソースの管理 (.NET)](/visualstudio/ide/managing-application-resources-dotnet)
- [デスクトップ アプリケーションのリソース](../../../framework/resources/index.md)
