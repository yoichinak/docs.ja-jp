---
title: <bindings>
ms.date: 01/22/2018
ms.assetid: b62cd369-5409-4030-8490-9759a462dd3a
ms.openlocfilehash: 7cafd8c1ba96a4fa1014f3570413b4bb83f69766
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57474723"
---
# <a name="bindings"></a>\<bindings>

使用することができます、`bindings`標準およびカスタム バインドの Windows Communication Foundation (WCF) のコレクションを構成する要素。 各エントリは、その一意の `binding` 属性で識別できる `name` 要素です。 サービスは、`name` を使用してバインディングをリンクすることにより、バインディングを使用します。 [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 以降では、バインディングおよび動作に名前を付ける必要はありません。 既定の構成と無名のバインディングおよび動作の詳細については、「[簡略化された構成](../../../../../docs/framework/wcf/simplified-configuration.md)」と「[WCF サービスの構成を簡略化](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)」を参照してください。  
  
## <a name="system-provided-bindings"></a>システム指定のバインド
 
 システム指定のバインディングは、WCF メッセージ スタックの複雑さを隠蔽します。 システム指定のバインディングを使用しているアプリケーションは、スタックを完全に制御する必要はありません。 システム指定の各バインディングに公開される属性は、バインディングが処理する使用シナリオに最適な属性です。  
  
 システム指定の各バインディングの構成セクションは、バインディングの構成に使用される複数の構成を定義できます。 各構成は、一意の名前によって識別されます。  
  
 システム指定のバインディングに要素または属性を追加することはできません。 これを行うに」の説明に従って、カスタム バインドを実装する必要があります、[カスタム バインド](#custom-bindings)セクション。 システム指定のバインディングを完全には、ユーザー アプリケーションは、上でコントロールを持つ必要があるいくつかの設定を追加するカスタム バインドを定義することになります。  
  
 システム指定のバインディングの一覧は、[System-Provided Bindings](../../../../../docs/framework/wcf/system-provided-bindings.md)を参照してください。  
  
## <a name="custom-bindings"></a>カスタム バインド

 カスタム バインディングを使用すると、WCF メッセージ スタックのフル コントロールが可能になります。 個別のバインディングは、メッセージ スタックを、スタック要素の構成要素をスタックに出現する順序で指定することにより定義します。 各要素は、定義して、スタックの 1 つの要素を構成します。 各カスタム バインディング内の `transport` 要素は 1 つだけにする必要があります。 この要素がない場合、メッセージ スタックは不完全です。  
  
 要素がスタックに出現する順序は重要です。それは、その順序で操作がメッセージに適用されるためです。 スタック要素で必要な順序を次に示します。  
  
1.  トランザクション (省略可能)  
  
2.  信頼性の高いメッセージング (省略可能)  
  
3.  セキュリティ (省略可能)  
  
4.  エンコーダー  
  
5.  Transport  
  
 カスタム バインドは、`name` 属性によって識別されます。 カスタム バインドの詳細については、[カスタム バインド](../../../../../docs/framework/wcf/extending/custom-bindings.md)を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Configuration.BindingsSection?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.Binding?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType>  
- [バインディング](../../../../../docs/framework/wcf/bindings.md)  
- [カスタム バインディング](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
- [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
- [\<binding>](../../../../../docs/framework/misc/binding.md)
