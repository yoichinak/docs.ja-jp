---
title: My.WebServices オブジェクト
ms.date: 07/20/2015
f1_keywords:
- My.WebServices
- My.MyProject.WebServices
helpviewer_keywords:
- My.WebServices object
ms.assetid: f188dc05-2c75-41b6-bb68-122d1c3110a2
ms.openlocfilehash: 290d025985663bc45fe605a2e9904fc90fb2bc63
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350348"
---
# <a name="mywebservices-object"></a>My.WebServices オブジェクト
Provides properties for creating and accessing a single instance of each XML Web service referenced by the current project.  
  
## <a name="remarks"></a>Remarks  
 `My.WebServices` オブジェクトは、現在のプロジェクトにより参照されている各 Web サービスのインスタンスを提供します。 各インスタンスは要求に応じてインスタンス化されます。 これらの Web サービスには `My.WebServices` オブジェクトのプロパティを介してアクセスできます。 プロパティの名前は、プロパティがアクセスする Web サービスの名前と同じになります。 <xref:System.Web.Services.Protocols.SoapHttpClientProtocol> から継承されたクラスはすべて Web サービスです。 For information about adding Web services to a project, see [Accessing Application Web Services](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).  
  
 The `My.WebServices` object exposes only the Web services associated with the current project. It does not provide access to Web services declared in referenced DLLs. To access a Web service that a DLL provides, you must use the qualified name of the Web service, in the form *DllName*.*WebServiceName*. For more information, see [Accessing Application Web Services](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).  
  
 The object and its properties are not available for Web applications.  
  
## <a name="properties"></a>プロパティ  
 Each property of the `My.WebServices` object provides access to an instance of a Web service referenced by the current project. The name of the property is the same as the name of the Web service that the property accesses, and the property type is the same as the Web service's type.  
  
> [!NOTE]
> If there is a name collision, the property name for accessing a Web service is *RootNamespace*_*Namespace*\_*ServiceName*. For example, consider two Web services named `Service1`. If one of these services is in the root namespace `WindowsApplication1` and in the namespace `Namespace1`, you would access that service by using `My.WebServices.WindowsApplication1_Namespace1_Service1`.  
  
 When you first access one of the `My.WebServices` object's properties, it creates a new instance of the Web service and stores it. Subsequent accesses of that property return that instance of the Web service.  
  
 You can dispose of a Web service by assigning `Nothing` to the property for that Web service. The property setter assigns `Nothing` to the stored value. If you assign any value other than `Nothing` to the property, the setter throws an <xref:System.ArgumentException> exception.  
  
 You can test whether a property of the `My.WebServices` object stores an instance of the Web service by using the `Is` or `IsNot` operator. You can use those operators to check if the value of the property is `Nothing`.  
  
> [!NOTE]
> Typically, the `Is` or `IsNot` operator has to read the value of the property to perform the comparison. However, if the property currently stores `Nothing`, the property creates a new instance of the Web service and then returns that instance. However, the Visual Basic compiler treats the properties of the `My.WebServices` object specially, and allows the `Is` or `IsNot` operator to check the status of the property without altering its value.  
  
## <a name="example"></a>例  
 This example calls the `FahrenheitToCelsius` method of the `TemperatureConverter` XML Web service, and returns the result.  
  
 [!code-vb[VbVbalrMyWebService#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWebService/VB/Form1.vb#1)]  
  
 For this example to work, your project must reference a Web service named `Converter`, and that Web service must expose the `ConvertTemperature` method. For more information, see [Accessing Application Web Services](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).  
  
 This code does not work in a Web application project.  
  
## <a name="requirements"></a>［要件］  
  
### <a name="availability-by-project-type"></a>Availability by Project Type  
  
|プロジェクトの種類|使用可能|  
|---|---|  
|Windows アプリケーション|**はい**|  
|クラス ライブラリ|**はい**|  
|コンソール アプリケーション|**はい**|  
|Windows Control Library|**はい**|  
|Web Control Library|**はい**|  
|Windows サービス|**はい**|  
|Web サイト|Ｘ|  
  
## <a name="see-also"></a>関連項目

- <xref:System.Web.Services.Protocols.SoapHttpClientProtocol>
- <xref:System.ArgumentException>
- [アプリケーションの Web サービスへのアクセス](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)
