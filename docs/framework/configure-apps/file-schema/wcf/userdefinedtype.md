---
title: <userDefinedType>
ms.date: 03/30/2017
ms.assetid: 0f70ec06-8249-4f0c-9f49-b4df59985fb8
ms.openlocfilehash: d1a48fa2ed90999a66f4c1f84b7cfaa9a0e79f6a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940579"
---
# <a name="userdefinedtype"></a>\<userDefinedType >
サービス コントラクトに含まれるユーザー定義型 (UDT) を表します。  
  
 \<system.ServiceModel >  
\<comContracts>  
\<comContract >  
\<userDefinedTypes >  
  
## <a name="syntax"></a>構文  
  
```xml  
<comContracts>
  <comContract>
    <userDefinedTypes>
      <userDefinedType name="String"
                       typeLibID="String"
                       typeLibVersion="String"
                       typeDefID="String">
      </userDefinedType>
    </userDefinedTypes>
  </comContract>
</comContracts>
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`name`|判読可能な型名を提供する文字列を含む省略可能な属性。 これは、ランタイムでは使用されませんが、リーダーが型を区別するのに役立ちます。|  
|`TypeDefID`|登録されているタイプ ライブラリ内の特定の UDT 型を識別する GUID 文字列。|  
|`TypeLibID`|型を定義する登録されているタイプ ライブラリを識別する GUID 文字列。|  
|`TypeLibVersion`|型を定義するタイプ ライブラリ バージョンを識別する文字列。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`userDefinedTypes`|`userDefinedType` 要素のコレクション。|  
  
## <a name="remarks"></a>Remarks  
 COM+ 統合ランタイムは、タイプ ライブラリを調べることによってサービスを作成します。 COM+ コンポーネントに VARIANT を渡すメソッドが含まれている場合、システムでは、渡される実際の型を実行前に判断することはできません。 したがって、VARIANT としてユーザー定義型 (UDT) を渡そうとしても、シリアル化で認識できる型ではないので失敗します。  
  
 この問題を回避するには、UDT を構成ファイルに追加して、適切なサービス コントラクトで既知の型として含まれるようにすることができます。 このためには、UDT およびコントラクト、つまりそれを使用する元の COM インターフェイスを一意に識別する必要があります。  
  
 次の例では、この目的のために`userDefinedTypes`、構成ファイルの < > セクションに2つの特定の udt を追加する方法を示します。  
  
```xml  
<comContracts>
  <comContract contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"
               namespace="http://tempuri.org/5163B1E7-F0CF-4B6A-9A02-4AB654F34284"
               name="_Broker"
               requireSession="true">
    <userDefinedTypes>
      <userDefinedType name="CustomerType"
                       typeLibID="{91DC728C-4F1A-45de-A9B6-B538E209CEA6}"
                       typeLibVersion="1.0"
                       typeDefID="{D129765C-F211-434e-825A-9A63198C41F2}">
      </userDefinedType>
      <userDefinedType name="AddressType"
                       typeLibID="{91DC728C-4F1A-45de-A9B6-B538E209CEA6}"
                       typeLibVersion="1.0"
                       typeDefID="{4616AE0D-687A-43B7-BC63-141AE3DFD099}">
      </userDefinedType>
    </userDefinedTypes>
    <exposedMethods>
      <exposedMethod name="BuyStock" />
      <exposedMethod name="SellStock" />
      <exposedMethod name="ExecuteTransaction" />
    </exposedMethods>
  </comContract>
</comContracts>
```  
  
 サービスを初期化する場合、統合ランタイムは、指定された型を検索し、指定されたコントラクトで既知の型のコレクションにそれらを追加します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Configuration.ComContractElement.UserDefinedTypes%2A>
- <xref:System.ServiceModel.Configuration.ComUdtElementCollection>
- <xref:System.ServiceModel.Configuration.ComUdtElement>
- [\<comContracts>](comcontracts.md)
- [COM+ アプリケーションとの統合](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [方法: COM + サービス設定の構成](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
