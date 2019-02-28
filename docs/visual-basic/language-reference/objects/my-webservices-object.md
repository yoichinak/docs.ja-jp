---
title: My.WebServices オブジェクト (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.WebServices
- My.MyProject.WebServices
helpviewer_keywords:
- My.WebServices object
ms.assetid: f188dc05-2c75-41b6-bb68-122d1c3110a2
ms.openlocfilehash: 1b4e703cb3f723ea283f725d0f4ce4711dca3c9e
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967816"
---
# <a name="mywebservices-object"></a>My.WebServices オブジェクト
プロパティは、作成して、現在のプロジェクトによって参照される各 XML Web サービスの 1 つのインスタンスへのアクセスを提供します。  
  
## <a name="remarks"></a>Remarks  
 `My.WebServices` オブジェクトは、現在のプロジェクトにより参照されている各 Web サービスのインスタンスを提供します。 各インスタンスは要求に応じてインスタンス化されます。 これらの Web サービスには `My.WebServices` オブジェクトのプロパティを介してアクセスできます。 プロパティの名前は、プロパティがアクセスする Web サービスの名前と同じになります。 <xref:System.Web.Services.Protocols.SoapHttpClientProtocol> から継承されたクラスはすべて Web サービスです。 Web サービスをプロジェクトに追加する方法の詳細については、次を参照してください。[にアクセスするアプリケーションの Web サービス](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)します。  
  
 `My.WebServices`オブジェクトは、現在のプロジェクトに関連付けられている Web サービスのみを公開します。 参照される Dll で宣言されている Web サービスへのアクセスは行いません。 DLL を提供する Web サービスにアクセスするには、フォームで、Web サービスの修飾名を使用する必要があります*DllName*.*WebServiceName*します。 詳細については、次を参照してください。[にアクセスするアプリケーションの Web サービス](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)します。  
  
 オブジェクトとそのプロパティでは、Web アプリケーションを使用できません。  
  
## <a name="properties"></a>プロパティ  
 各プロパティ、`My.WebServices`オブジェクトは、現在のプロジェクトによって参照される Web サービスのインスタンスへのアクセスを提供します。 プロパティの名前が同じプロパティがアクセスする Web サービスの名前とプロパティの型が、Web サービスの型と同じです。  
  
> [!NOTE]
>  Web サービスにアクセスするためのプロパティ名は、名前の競合がある場合*RootNamespace*_*Namespace*\_*ServiceName*します。 たとえば、という名前の 2 つの Web サービス`Service1`します。 ルート名前空間ではこれらのサービスのいずれかのかどうかは`WindowsApplication1`と名前空間に`Namespace1`を使用して、そのサービスにアクセス`My.WebServices.WindowsApplication1_Namespace1_Service1`します。  
  
 初めてアクセスしたときの 1 つ、`My.WebServices`オブジェクトのプロパティでは、Web サービスの新しいインスタンスを作成し、格納します。 そのプロパティの後続のアクセスは、Web サービスのインスタンスを返します。  
  
 Web サービスを処分するには、割り当てることで`Nothing`をその Web サービスのプロパティ。 プロパティ set アクセス操作子を割り当てます`Nothing`に格納されている値。 以外の任意の値を割り当てた場合`Nothing`プロパティの setter がスローされます、<xref:System.ArgumentException>例外。  
  
 プロパティかどうかをテストすることができます、`My.WebServices`オブジェクトを使用して、Web サービスのインスタンスを格納する、`Is`または`IsNot`演算子。 これらの演算子を使用するには、プロパティの値をチェックする`Nothing`します。  
  
> [!NOTE]
>  通常、`Is`または`IsNot`オペレーターは、比較を実行するプロパティの値を読み取ることがあります。 ただし、プロパティが現在格納されている場合`Nothing`プロパティ、Web サービスの新しいインスタンスを作成し、し、そのインスタンスを返します。 ただし、Visual Basic コンパイラがのプロパティを処理、`My.WebServices`でき、特別に、オブジェクト、`Is`または`IsNot`演算子をその値を変更することがなく、プロパティの状態を確認します。  
  
## <a name="example"></a>例  
 この例では、`FahrenheitToCelsius`のメソッド、 `TemperatureConverter` XML Web サービスでは、結果を返します。  
  
 [!code-vb[VbVbalrMyWebService#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWebService/VB/Form1.vb#1)]  
  
 この例を動作させるには、プロジェクトがという名前の Web サービスを参照する必要があります`Converter`、し、その Web サービスを公開する必要があります、`ConvertTemperature`メソッド。 詳細については、次を参照してください。[にアクセスするアプリケーションの Web サービス](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)します。  
  
 このコードは、Web アプリケーション プロジェクトでは機能しません。  
  
## <a name="requirements"></a>必要条件  
  
### <a name="availability-by-project-type"></a>プロジェクトの種類ごとの可用性  
  
|プロジェクトの種類|使用可能|  
|---|---|  
|Windows アプリケーション|**はい**|  
|クラス ライブラリ|**はい**|  
|コンソール アプリケーション|**はい**|  
|Windows コントロール ライブラリ|**はい**|  
|Web コントロール ライブラリ|**はい**|  
|Windows サービス|**はい**|  
|Web サイト|いいえ|  
  
## <a name="see-also"></a>関連項目
- <xref:System.Web.Services.Protocols.SoapHttpClientProtocol>
- <xref:System.ArgumentException>
- [アプリケーションの Web サービスへのアクセス](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)
