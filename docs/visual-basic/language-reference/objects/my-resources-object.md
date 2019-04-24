---
title: My.Resources オブジェクト (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.Resources
- My.Resources.MyResources.ResourceManager
- My.Resources.MyResources.Culture
helpviewer_keywords:
- My.Resources object
ms.assetid: 34c3f2dc-7b87-432c-9d5f-17ea666bb266
ms.openlocfilehash: ee4d30b82ceada5c4f3fc4ad95dc8eeedd9355b0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58821739"
---
# <a name="myresources-object"></a>My.Resources オブジェクト
アプリケーションのリソースにアクセスするためのプロパティとクラスを提供します。  
  
## <a name="remarks"></a>Remarks  
 `My.Resources`オブジェクト、アプリケーションのリソースへのアクセスを提供でき、動的にアプリケーションのリソースを取得します。 詳細については、次を参照してください。[アプリケーション リソースの管理 (.NET)](/visualstudio/ide/managing-application-resources-dotnet)します。  
  
 `My.Resources`オブジェクトはグローバル リソースのみを公開します。 フォームに関連付けられているリソース ファイルへのアクセスは行いません。 フォームのフォーム リソースにアクセスする必要があります。  
  
 アプリケーションのカルチャ固有のリソース ファイルにアクセスすることができます、`My.Resources`オブジェクト。 既定で、`My.Resources`オブジェクトのカルチャに一致するリソース ファイルからリソースを調べ、<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.UICulture%2A>プロパティ。 ただし、この動作をオーバーライドし、リソースに使用する特定のカルチャを指定できます。 詳細については、「[デスクトップ アプリケーションのリソース](../../../framework/resources/index.md)」を参照してください。  
  
## <a name="properties"></a>プロパティ  
 プロパティ、`My.Resources`オブジェクトは、アプリケーションのリソースへの読み取り専用アクセスを提供します。 を追加または削除のリソースを使用して、**プロジェクト デザイナー**します。 使用して追加のリソースにアクセスすることができます、**プロジェクト デザイナー**を使用して`My.Resources.` *resourceName*します。  
  
 追加またはでプロジェクトを選択してリソース ファイルを削除することができますも**ソリューション エクスプ ローラー**クリック**新しい項目の追加**または**既存項目の追加**から、 **プロジェクト**メニュー。 使用して、この方法で追加のリソースにアクセスすることができます`My.Resources.` *resourceFileName*`.`*resourceName*します。  
  
 各リソースには、名前、カテゴリ、および値、およびこれらのリソースの設定は、リソースにアクセスするプロパティを表示する方法を決定、`My.Resources`オブジェクト。 追加するリソースの**プロジェクト デザイナー**:  
  
-   名前は、プロパティの名前を決定します。  
  
-   リソース データは、プロパティの値  
  
-   カテゴリは、プロパティの型を決定します。  
  
|Category|プロパティのデータ型|  
|---|---|  
|**文字列**|[String](../../../visual-basic/language-reference/data-types/string-data-type.md)|  
|**イメージ**|<xref:System.Drawing.Bitmap>|  
|**アイコン**|<xref:System.Drawing.Icon>|  
|**オーディオ**|<xref:System.IO.UnmanagedMemoryStream><br /><br /> <xref:System.IO.UnmanagedMemoryStream>クラスから派生、<xref:System.IO.Stream>クラス、メソッドなど、ストリームを確認すると、使用できるように、<xref:Microsoft.VisualBasic.Devices.Audio.Play%2A>メソッド。|  
|**ファイル**|-   [文字列](../../../visual-basic/language-reference/data-types/string-data-type.md)テキスト ファイル。<br />-   <xref:System.Drawing.Bitmap> イメージ ファイル。<br />-   <xref:System.Drawing.Icon> アイコン ファイル。<br />-   <xref:System.IO.UnmanagedMemoryStream> 音声ファイル。|  
|**その他**|デザイナーの内の情報によって決まります**型**列。|  
  
## <a name="classes"></a>クラス  
 `My.Resources`オブジェクト クラスと共有のプロパティとして各リソース ファイルを公開します。 クラス名は、リソース ファイルの名前と同じです。 前のセクションで説明した、リソース ファイル内のリソースは、クラスのプロパティとして公開されます。  
  
## <a name="example"></a>例  
 この例では、指定された文字列リソースをフォームのタイトルを設定`Form1Title`アプリケーション リソース ファイルにします。 例を動作させるには、アプリケーションがという名前の文字列をいる必要があります`Form1Title`リソース ファイル。  
  
 [!code-vb[VbVbalrMyResources#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#1)]  
  
## <a name="example"></a>例  
 この例では、フォームのアイコンを設定するという名前のアイコン`Form1Icon`アプリケーションのリソース ファイルに格納されています。 例を動作させるには、アプリケーションがという名前のアイコンをいる必要があります`Form1Icon`リソース ファイル。  
  
 [!code-vb[VbVbalrMyResources#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#2)]  
  
## <a name="example"></a>例  
 この例では、フォームの背景イメージを設定という名前のイメージ リソースを`Form1Background`、アプリケーション リソース ファイルであります。 この例を動作させるには、アプリケーションがという名前のイメージ リソースを必要`Form1Background`リソース ファイル。  
  
 [!code-vb[VbVbalrMyResources#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#3)]  
  
## <a name="example"></a>例  
 この例は、オーディオという名前のリソースとして格納されているサウンドを再生`Form1Greeting`でアプリケーションのリソース ファイル。 例を動作させるには、アプリケーションにオーディオという名前のリソースが必要`Form1Greeting`リソース ファイル。 `My.Computer.Audio.Play`メソッドは Windows フォーム アプリケーションでのみ使用できます。  
  
 [!code-vb[VbVbalrMyResources#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#4)]  
  
## <a name="example"></a>例  
 この例では、アプリケーションの文字列リソースのフランス語のカルチャのバージョンを取得します。 リソースが名前付き`Message`します。 カルチャを変更するが、`My.Resources`オブジェクトを使用して、この例では<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.ChangeUICulture%2A>します。  
  
 この例を動作させるには、アプリケーションがという名前の文字列をいる必要があります`Message`でのリソース ファイル、およびアプリケーションが必要にリソース ファイルで、Resources.fr-fr.resx のフランス語のカルチャのバージョン。 アプリケーションには、リソース ファイルのフランス語のカルチャのバージョンがない場合、`My.Resource`オブジェクトは、既定のカルチャのリソース ファイルからリソースを取得します。  
  
 [!code-vb[VbVbalrMyResources#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#10)]  
  
## <a name="see-also"></a>関連項目

- [アプリケーション リソースの管理 (.NET)](/visualstudio/ide/managing-application-resources-dotnet)
- [デスクトップ アプリケーションのリソース](../../../framework/resources/index.md)
