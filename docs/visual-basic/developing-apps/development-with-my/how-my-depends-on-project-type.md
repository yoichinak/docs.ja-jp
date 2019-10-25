---
title: プロジェクトの種類に応じた My の機能 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- _MYTYPE
ms.assetid: c188b38e-bd9d-4121-9983-41ea6a94d28e
ms.openlocfilehash: 989329da7dc57cd50b9ce6c88117152d0cb93d66
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775196"
---
# <a name="how-my-depends-on-project-type-visual-basic"></a>プロジェクトの種類に応じた My の機能 (Visual Basic)
`My` は、特定のプロジェクトの種類に必要なオブジェクトのみを公開します。 たとえば、`My.Forms` オブジェクトは Windows フォームアプリケーションで使用できますが、コンソールアプリケーションでは使用できません。 このトピックでは、さまざまなプロジェクトの種類で使用できる `My` オブジェクトについて説明します。  
  
## <a name="my-in-windows-applications-and-web-sites"></a>Windows アプリケーションと Web サイトの My  
 `My` は、現在のプロジェクトの種類で有用なオブジェクトのみを公開します。適用できないオブジェクトは抑制されます。 たとえば、次の図は、Windows フォームプロジェクトの `My` オブジェクトモデルを示しています。  
  
 ![Windows フォームアプリケーションの My オブジェクトモデルを示す図](./media/how-my-depends-on-project-type/my-object-model-windows-forms.png)  
  
 Web サイトプロジェクトでは、`My` は、関連のないオブジェクト (`My.Forms` オブジェクトなど) を抑制しながら、Web 開発者に関連するオブジェクト (`My.Request`、`My.Response` オブジェクトなど) を公開します。 次の図は、Web サイトプロジェクトの `My` オブジェクトモデルを示しています。  
  
 ![Web アプリケーションの My オブジェクトモデルを示す図](./media/how-my-depends-on-project-type/my-object-model-web.png)  
  
## <a name="project-details"></a>プロジェクトの詳細  
 次の表は、8種類のプロジェクトで既定で有効になっている `My` オブジェクト (Windows アプリケーション、クラスライブラリ、コンソールアプリケーション、Windows コントロールライブラリ、Web コントロールライブラリ、Windows サービス、空、Web サイト) を示しています。  
  
 @No__t_0 オブジェクトには3つのバージョン、`My.Computer` オブジェクトの2つのバージョン、および `My.User` オブジェクトの2つのバージョンがあります。これらのバージョンの詳細については、表の後の脚注に記載されています。  
  
|マイオブジェクト|Windows アプリケーション|クラス ライブラリ|コンソール アプリケーション|Windows コントロールライブラリ|Web コントロールライブラリ|Windows サービス|Empty|Web サイト|  
|---|---|---|---|---|---|---|---|---|  
|`My.Application`|**はい** <sup>1</sup>|**はい** <sup>2</sup>|**はい** <sup>3</sup>|**はい** <sup>2</sup>|Ｘ|**はい** <sup>3</sup>|Ｘ|Ｘ|  
|`My.Computer`|**はい** <sup>4</sup>|**はい** <sup>4</sup>|**はい** <sup>4</sup>|**はい** <sup>4</sup>|**可** <sup>5</sup>|**はい** <sup>4</sup>|Ｘ|**可** <sup>5</sup>|  
|`My.Forms`|**はい**|Ｘ|Ｘ|**はい**|Ｘ|Ｘ|Ｘ|Ｘ|  
|`My.Log`|Ｘ|Ｘ|Ｘ|Ｘ|Ｘ|Ｘ|Ｘ|**はい**|  
|`My.Request`|Ｘ|Ｘ|Ｘ|Ｘ|Ｘ|Ｘ|Ｘ|**はい**|  
|`My.Resources`|**はい**|**はい**|**はい**|**はい**|**はい**|**はい**|Ｘ|Ｘ|  
|`My.Response`|Ｘ|Ｘ|Ｘ|Ｘ|Ｘ|Ｘ|Ｘ|**はい**|  
|`My.Settings`|**はい**|**はい**|**はい**|**はい**|**はい**|**はい**|Ｘ|Ｘ|  
|`My.User`|**はい** <sup>6</sup>|**はい** <sup>6</sup>|**はい** <sup>6</sup>|**はい** <sup>6</sup>|**○** <sup>7</sup>|**はい** <sup>6</sup>|Ｘ|**○** <sup>7</sup>|  
|`My.WebServices`|**はい**|**はい**|**はい**|**はい**|**はい**|**はい**|Ｘ|Ｘ|  
  
 <sup>1</sup> Windows フォームバージョンの `My.Application`。 コンソールのバージョンから派生します (注3を参照)。アプリケーションのウィンドウと対話するためのサポートを追加し、Visual Basic アプリケーションモデルを提供します。  
  
 <sup>2</sup>ライブラリバージョンの `My.Application`。 アプリケーションに必要な基本機能を提供します。アプリケーションログへの書き込みおよびアプリケーション情報へのアクセスのためのメンバーを提供します。  
  
 `My.Application` の<sup>3</sup>コンソールバージョン。 は、ライブラリバージョンから派生し (メモ2を参照)、アプリケーションのコマンドライン引数および ClickOnce 配置情報にアクセスするためのメンバーを追加します。  
  
 <sup>4</sup> Windows バージョンの `My.Computer`。 サーバーのバージョンから派生します (注5を参照)。また、キーボード、画面、マウスなど、クライアントコンピューター上の便利なオブジェクトへのアクセスを提供します。  
  
 `My.Computer` の<sup>5 台</sup>のサーバーバージョン。 名前、時計へのアクセスなど、コンピューターに関する基本的な情報を提供します。  
  
 <sup>6</sup> Windows バージョンの `My.User`。 このオブジェクトは、スレッドの現在の id に関連付けられています。  
  
 <sup>7</sup> Web バージョンの `My.User`。 このオブジェクトは、アプリケーションの現在の HTTP 要求のユーザー id に関連付けられています。  
  
## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.Logging.Log>
- <xref:Microsoft.VisualBasic.ApplicationServices.User>
- [My で利用可能なオブジェクトのカスタマイズ](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
- [条件付きコンパイル](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- [-define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)
- [My.Forms オブジェクト](../../../visual-basic/language-reference/objects/my-forms-object.md)
- [My.Request オブジェクト](../../../visual-basic/language-reference/objects/my-request-object.md)
- [My.Response オブジェクト](../../../visual-basic/language-reference/objects/my-response-object.md)
- [My.WebServices オブジェクト](../../../visual-basic/language-reference/objects/my-webservices-object.md)
