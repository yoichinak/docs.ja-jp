---
title: My で利用可能なオブジェクトのカスタマイズ (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
ms.assetid: 4e8279c2-ed5b-4681-8903-8a6671874000
ms.openlocfilehash: c0b47521c6a62071466ae4193cd8553bdfb3dcde
ms.sourcegitcommit: 5c2176883dc3107445702724a7caa7ac2f6cb0d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/03/2019
ms.locfileid: "58890372"
---
# <a name="customizing-which-objects-are-available-in-my-visual-basic"></a>My で利用可能なオブジェクトのカスタマイズ (Visual Basic)

このトピックでは、これを制御する方法について説明します`My`オブジェクトは、プロジェクトの設定で有効になって`_MYTYPE`条件付きコンパイル定数。 Visual Studio 統合開発環境 (IDE) の保持、`_MYTYPE`プロジェクト、プロジェクトの種類と同期するための条件付きコンパイル定数。  
  
## <a name="predefined-mytype-values"></a>定義済みの\_MYTYPE の値  

使用する必要があります、`/define`コンパイラ オプションを設定する、`_MYTYPE`条件付きコンパイル定数。 独自の値を指定するときに、 `_MYTYPE` 、定数で囲んでください。 文字列値バック スラッシュ/引用符 (\\") のシーケンス。 たとえば、次のように使用する可能性があります。  
  
```  
/define:_MYTYPE=\"WindowsForms\"  
```  
  
 この表ではどのような`_MYTYPE`プロジェクトの種類をいくつかの条件付きコンパイル定数に設定されます。  
  
|プロジェクトの種類|\_MYTYPE の値|  
|------------------|--------------------|  
|クラス ライブラリ|"Windows"|  
|コンソール アプリケーション|「コンソール」|  
|Web|"Web"|  
|Web コントロール ライブラリ|"WebControl"|  
|Windows アプリケーション|"WindowsForms"|  
|ユーザー設定を開始するときに、Windows アプリケーション `Sub Main`|"WindowsFormsWithCustomSubMain"|  
|Windows コントロール ライブラリ|"Windows"|  
|Windows サービス|「コンソール」|  
|Empty|「空」|  
  
> [!NOTE]
> すべての条件付きコンパイルの文字列比較は関係なく大文字/小文字`Option Compare`ステートメントを設定します。  
  
## <a name="dependent-my-compilation-constants"></a>依存\_マイ コンパイル定数  

`_MYTYPE`条件付きコンパイル定数の場合、さらに、その他のいくつかの値を制御`_MY`コンパイル定数。  
  
|\_MYTYPE|\_MYAPPLICATIONTYPE|\_MYCOMPUTERTYPE|\_MYFORMS|\_MYUSERTYPE|\_MYWEBSERVICES|  
|--------------|-------------------------|----------------------|---------------|------------------|---------------------|  
|「コンソール」|「コンソール」|"Windows"|未定義|"Windows"|true|  
|"Custom"|未定義|未定義|未定義|未定義|未定義|  
|「空」|未定義|未定義|未定義|未定義|未定義|  
|"Web"|未定義|"Web"|false|"Web"|false|  
|"WebControl"|未定義|"Web"|false|"Web"|true|  
|"Windows"または""|"Windows"|"Windows"|未定義|"Windows"|true|  
|"WindowsForms"|"WindowsForms"|"Windows"|true|"Windows"|true|  
|"WindowsFormsWithCustomSubMain"|「コンソール」|"Windows"|true|"Windows"|true|  
  
 既定では、未定義の条件付きコンパイル定数を解決する`FALSE`します。 既定の動作をオーバーライドするようにプロジェクトをコンパイルするときに、未定義の定数の値を指定できます。  
  
> [!NOTE]
> ときに`_MYTYPE`設定が"Custom"にプロジェクトに含まれる、`My`が名前空間が含まれていないオブジェクトには。 ただし、設定`_MYTYPE`を追加できない、"Empty"のように、コンパイラ、`My`名前空間とそのオブジェクト。  
  
 このテーブルの定義済みの値の効果の説明、`_MY`コンパイル定数。  
  
|定数|説明|  
|--------------|-------------|  
|`_MYAPPLICATIONTYPE`|により、`My.Application`定数は、「コンソールの」、Windows の場合は、"または"WindowsForms"。<br /><br /> -「コンソール」バージョンから派生した<xref:Microsoft.VisualBasic.ApplicationServices.ConsoleApplicationBase>します。 "Windows"のバージョンよりも少ないメンバーです。<br />-"Windows"のバージョンから派生した<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>それから"WindowsForms"バージョンよりも少ないメンバーを持ちます。<br />-"WindowsForms"バージョンの`My.Application`から派生した<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>します。 場合、 `TARGET` "winexe"を指定する定数を定義し、クラスが含まれています、`Sub Main`メソッド。|  
|`_MYCOMPUTERTYPE`|により、`My.Computer`定数が"Web"または"Windows"の場合。<br /><br /> -"Web"のバージョンから派生した<xref:Microsoft.VisualBasic.Devices.ServerComputer>、"Windows"のバージョンよりも少ないメンバーを持つとします。<br />-"Windows"のバージョンの`My.Computer`から派生した<xref:Microsoft.VisualBasic.Devices.Computer>します。|  
|`_MYFORMS`|により、`My.Forms`定数の場合、`TRUE`します。|  
|`_MYUSERTYPE`|により、`My.User`定数が"Web"または"Windows"の場合。<br /><br /> -の"Web"バージョン`My.User`は現在の HTTP 要求のユーザー id に関連付けられています。<br />-"Windows"のバージョンの`My.User`スレッドの現在のプリンシパルに関連付けられています。|  
|`_MYWEBSERVICES`|により、`My.WebServices`定数の場合、`TRUE`します。|  
|`_MYTYPE`|により、 `My.Log`、 `My.Request`、および`My.Response`定数が"Web"の場合。|  
  
## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.Logging.Log>
- <xref:Microsoft.VisualBasic.ApplicationServices.User>
- [プロジェクトの種類に応じた My の機能](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)
- [条件付きコンパイル](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- [/define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)
- [My.Forms オブジェクト](../../../visual-basic/language-reference/objects/my-forms-object.md)
- [My.Request オブジェクト](../../../visual-basic/language-reference/objects/my-request-object.md)
- [My.Response オブジェクト](../../../visual-basic/language-reference/objects/my-response-object.md)
- [My.WebServices オブジェクト](../../../visual-basic/language-reference/objects/my-webservices-object.md)
