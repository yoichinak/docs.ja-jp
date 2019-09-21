---
title: My.user オブジェクト (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.WebServices
- My.MyProject.WebServices
helpviewer_keywords:
- My.WebServices object
ms.assetid: f188dc05-2c75-41b6-bb68-122d1c3110a2
ms.openlocfilehash: c887f9b7c5a41c0aa02016354c46d5507b103d25
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918180"
---
# <a name="mywebservices-object"></a>My.WebServices オブジェクト
現在のプロジェクトによって参照される各 XML Web サービスの1つのインスタンスを作成してアクセスするためのプロパティを提供します。  
  
## <a name="remarks"></a>Remarks  
 `My.WebServices` オブジェクトは、現在のプロジェクトにより参照されている各 Web サービスのインスタンスを提供します。 各インスタンスは要求に応じてインスタンス化されます。 これらの Web サービスには `My.WebServices` オブジェクトのプロパティを介してアクセスできます。 プロパティの名前は、プロパティがアクセスする Web サービスの名前と同じになります。 <xref:System.Web.Services.Protocols.SoapHttpClientProtocol> から継承されたクラスはすべて Web サービスです。 プロジェクトへの Web サービスの追加については、「[アプリケーション Web サービス](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)へのアクセス」を参照してください。  
  
 オブジェクト`My.WebServices`は、現在のプロジェクトに関連付けられている Web サービスだけを公開します。 参照先の Dll で宣言されている Web サービスへのアクセスを提供しません。 DLL が提供する Web サービスにアクセスするには、Web サービスの修飾名を*DllName*の形式で使用する必要があります。*Webservicename*。 詳細については、「[アプリケーション Web サービスへのアクセス](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)」を参照してください。  
  
 オブジェクトとそのプロパティは、Web アプリケーションでは使用できません。  
  
## <a name="properties"></a>プロパティ  
 `My.WebServices`オブジェクトの各プロパティは、現在のプロジェクトによって参照されている Web サービスのインスタンスへのアクセスを提供します。 プロパティの名前は、プロパティがアクセスする Web サービスの名前と同じです。プロパティの型は、Web サービスの型と同じです。  
  
> [!NOTE]
> 名前の競合がある場合、Web サービスにアクセスするためのプロパティ名は*RootNamespace*_*Namespace*\_*ServiceName*です。 たとえば、という名前`Service1`の2つの Web サービスを考えてみます。 これらのサービスのいずれかがルート名前空間`WindowsApplication1`および名前空間`Namespace1`にある場合は、を使用`My.WebServices.WindowsApplication1_Namespace1_Service1`してそのサービスにアクセスします。  
  
 `My.WebServices`オブジェクトのいずれかのプロパティに初めてアクセスすると、Web サービスの新しいインスタンスが作成され、保存されます。 そのプロパティの後続のアクセスでは、Web サービスのインスタンスが返されます。  
  
 Web サービスのプロパティにを割り当てる`Nothing`ことによって、web サービスを破棄できます。 プロパティ set アクセス操作`Nothing`子は、格納されている値に割り当てられます。 以外`Nothing`の値をプロパティに割り当てた場合、setter は<xref:System.ArgumentException>例外をスローします。  
  
 `Is`また`My.WebServices` は`IsNot`演算子を使用して、オブジェクトのプロパティに Web サービスのインスタンスが格納されているかどうかをテストできます。 これらの演算子を使用すると、プロパティの値がで`Nothing`あるかどうかを確認できます。  
  
> [!NOTE]
> 通常、 `Is`または`IsNot`演算子は、比較を実行するためにプロパティの値を読み取る必要があります。 ただし、プロパティが現在を格納`Nothing`している場合は、プロパティによって Web サービスの新しいインスタンスが作成され、そのインスタンスが返されます。 ただし、Visual Basic コンパイラは、 `My.WebServices`オブジェクトのプロパティを特別に処理し、または`IsNot`演算子が`Is`値を変更せずにプロパティの状態を確認できるようにします。  
  
## <a name="example"></a>例  
 この例では`FahrenheitToCelsius` 、 `TemperatureConverter` XML Web サービスのメソッドを呼び出し、その結果を返します。  
  
 [!code-vb[VbVbalrMyWebService#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWebService/VB/Form1.vb#1)]  
  
 この例を機能させるには、プロジェクトでという名前`Converter`の web サービスを参照し、その`ConvertTemperature` web サービスがメソッドを公開する必要があります。 詳細については、「[アプリケーション Web サービスへのアクセス](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)」を参照してください。  
  
 このコードは、Web アプリケーションプロジェクトでは機能しません。  
  
## <a name="requirements"></a>必要条件  
  
### <a name="availability-by-project-type"></a>プロジェクトの種類別の可用性  
  
|プロジェクトの種類|使用可能|  
|---|---|  
|Windows アプリケーション|**はい**|  
|クラス ライブラリ|**はい**|  
|コンソール アプリケーション|**はい**|  
|Windows コントロールライブラリ|**はい**|  
|Web コントロールライブラリ|**はい**|  
|Windows サービス|**はい**|  
|Web サイト|いいえ|  
  
## <a name="see-also"></a>関連項目

- <xref:System.Web.Services.Protocols.SoapHttpClientProtocol>
- <xref:System.ArgumentException>
- [アプリケーションの Web サービスへのアクセス](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)
