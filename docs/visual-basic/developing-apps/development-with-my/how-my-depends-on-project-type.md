---
title: プロジェクトの種類に応じた My の機能 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- _MYTYPE
ms.assetid: c188b38e-bd9d-4121-9983-41ea6a94d28e
ms.openlocfilehash: 72b9799d1f5ba7efa37d5f8f2a633e6806a58607
ms.sourcegitcommit: 89fcad7e816c12eb1299128481183f01c73f2c07
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "63808108"
---
# <a name="how-my-depends-on-project-type-visual-basic"></a>プロジェクトの種類に応じた My の機能 (Visual Basic)
`My` 特定のプロジェクトの種類で必要なオブジェクトのみを公開します。 たとえば、`My.Forms`オブジェクトは、Windows フォーム アプリケーションで使用できますが、コンソール アプリケーションでは使用できません。 このトピックで説明する`My`オブジェクトは異なる種類のプロジェクトで使用できます。  
  
## <a name="my-in-windows-applications-and-web-sites"></a>自分の Windows アプリケーションや Web サイト  
 `My` 現在、プロジェクトの種類の有用なオブジェクトのみを公開します。適用されないオブジェクトが抑制されます。 たとえば、次の図は、 `My` Windows フォーム プロジェクトでオブジェクト モデルです。  
  
 ![ダイアグラムを表示する、Windows フォーム アプリケーションでオブジェクト モデルです。](./media/how-my-depends-on-project-type/my-object-model-windows-forms.png)  
  
 Web サイト プロジェクトで`My`Web 開発者に関連するオブジェクトを公開します (など、`My.Request`と`My.Response`オブジェクト) 関連のないオブジェクトの抑制中に (など、`My.Forms`オブジェクト)。 次の図は、 `My` Web サイト プロジェクトのオブジェクト モデル。  
  
 ![示す図、Web アプリケーションでオブジェクト モデルです。](./media/how-my-depends-on-project-type/my-object-model-web.png)  
  
## <a name="project-details"></a>プロジェクトの詳細  
 次の表では`My`8 プロジェクトの種類のオブジェクトが既定で有効にします。Windows アプリケーション、クラス ライブラリ、コンソール アプリケーション、Windows コントロール ライブラリ、Web コントロール ライブラリ、Windows サービス、空、および Web サイト。  
  
 3 つのバージョンがある、`My.Application`オブジェクト、2 つのバージョン、`My.Computer`オブジェクト、および 2 つのバージョンの`My.User`オブジェクトです。 これらのバージョンの詳細については、表の後の脚注で与えられます。  
  
|My オブジェクト|Windows アプリケーション|クラス ライブラリ|コンソール アプリケーション|Windows コントロール ライブラリ|Web コントロール ライブラリ|Windows サービス|Empty|Web サイト|  
|---|---|---|---|---|---|---|---|---|  
|`My.Application`|**[はい]** <sup>1</sup>|**[はい]** <sup>2</sup>|**[はい]** <sup>3</sup>|**[はい]** <sup>2</sup>|いいえ|**[はい]** <sup>3</sup>|いいえ|いいえ|  
|`My.Computer`|**[はい]** <sup>4</sup>|**[はい]** <sup>4</sup>|**[はい]** <sup>4</sup>|**[はい]** <sup>4</sup>|**[はい]** <sup>5</sup>|**[はい]** <sup>4</sup>|いいえ|**[はい]** <sup>5</sup>|  
|`My.Forms`|**はい**|いいえ|いいえ|**はい**|いいえ|×|×|×|  
|`My.Log`|×|×|×|×|×|×|いいえ|**はい**|  
|`My.Request`|いいえ|×|×|×|×|×|いいえ|**はい**|  
|`My.Resources`|**はい**|**はい**|**はい**|**はい**|**はい**|**はい**|いいえ|×|  
|`My.Response`|×|×|×|×|×|×|いいえ|**はい**|  
|`My.Settings`|**はい**|**はい**|**はい**|**はい**|**はい**|**はい**|いいえ|いいえ|  
|`My.User`|**[はい]** <sup>6</sup>|**[はい]** <sup>6</sup>|**[はい]** <sup>6</sup>|**[はい]** <sup>6</sup>|**[はい]** <sup>7</sup>|**[はい]** <sup>6</sup>|いいえ|**[はい]** <sup>7</sup>|  
|`My.WebServices`|**はい**|**はい**|**はい**|**はい**|**はい**|**はい**|いいえ|いいえ|  
  
 <sup>1</sup>の Windows フォーム バージョン`My.Application`します。 コンソールのバージョンからの派生 (注 3 を参照してください)。アプリケーションの windows を操作するためのサポートが追加され、Visual Basic アプリケーション モデルを提供します。  
  
 <sup>2</sup>ライブラリ版の`My.Application`します。 アプリケーションで必要な基本的な機能を提供します。 アプリケーション ログへの書き込みと、アプリケーションの情報にアクセスするメンバーを提供します。  
  
 <sup>3</sup>のコンソール バージョン`My.Application`します。 ライブラリのバージョンからの派生 (注 2 を参照)、アプリケーションのコマンドライン引数と ClickOnce 配置の情報にアクセスするための追加メンバーを追加します。  
  
 <sup>4</sup>の Windows バージョン`My.Computer`します。 サーバーのバージョンからの派生元 (メモ 5 を参照)、し、キーボード、画面、マウスなどのクライアント コンピューターで役に立つオブジェクトへのアクセスを提供します。  
  
 <sup>5</sup>のサーバー バージョン`My.Computer`します。 名前、時計、およびなどへのアクセスなど、コンピューターに関する基本情報を提供します。  
  
 <sup>6</sup>の Windows バージョン`My.User`します。 このオブジェクトは、スレッドの現在の id に関連付けられます。  
  
 <sup>7</sup>の web バージョン`My.User`します。 このオブジェクトは、アプリケーションの現在の HTTP 要求のユーザー id に関連付けられます。  
  
## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.Logging.Log>
- <xref:Microsoft.VisualBasic.ApplicationServices.User>
- [My で利用可能なオブジェクトのカスタマイズ](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
- [条件付きコンパイル](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- [/define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)
- [My.Forms オブジェクト](../../../visual-basic/language-reference/objects/my-forms-object.md)
- [My.Request オブジェクト](../../../visual-basic/language-reference/objects/my-request-object.md)
- [My.Response オブジェクト](../../../visual-basic/language-reference/objects/my-response-object.md)
- [My.WebServices オブジェクト](../../../visual-basic/language-reference/objects/my-webservices-object.md)
