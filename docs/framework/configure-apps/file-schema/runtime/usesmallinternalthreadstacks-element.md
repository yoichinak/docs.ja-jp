---
title: <UseSmallInternalThreadStacks> 要素
ms.date: 03/30/2017
helpviewer_keywords:
- UseSmallInternalThreadStacks element
- <UseSmallInternalThreadStacks> element
ms.assetid: 1e3f6ec0-1cac-4e1c-9c81-17d948ae5874
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b9833d768b84faaf6e1dcf8c9cb8b00b92adc3d1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59144827"
---
# <a name="usesmallinternalthreadstacks-element"></a>\<UseSmallInternalThreadStacks > 要素
要求の共通言語ランタイム (CLR) がメモリを減らすことは、内部的には、これらのスレッドの既定のスタック サイズを使用する代わりに使用する特定のスレッドの作成時に、明示的なスタック サイズを指定することによって使用されます。  
  
 \<configuration > 要素  
\<ランタイム > 要素  
\<UseSmallInternalThreadStacks > 要素  
  
## <a name="syntax"></a>構文  
  
```xml  
<UseSmallInternalThreadStacks enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|enabled|必須の属性です。<br /><br /> 内部的に使用する特定のスレッドを作成するときを要求するかどうかに既定のスタック サイズではなく、CLR の使用の明示的なスタック サイズを指定します。 明示的なスタック サイズは 1 MB の既定のスタック サイズより小さいです。|  
  
## <a name="enabled-attribute"></a>enabled 属性  
  
|値|説明|  
|-----------|-----------------|  
|true|明示的なスタック サイズを要求します。|  
|False|既定のスタック サイズを使用します。 これは、既定値は、[!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]します。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。|  
  
## <a name="remarks"></a>Remarks  
 この構成要素は、CLR は、その内部のスレッドの場合は、要求が受け入れられます、明示的なスレッドのサイズが既定のサイズより小さいために、プロセスより少ない仮想メモリの使用を要求に使用されます。  
  
> [!IMPORTANT]
>  この構成要素は、絶対要件ではなく、CLR に要求です。 [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]X86 にのみ、要求が受け入れられますアーキテクチャ。 この要素は、CLR の将来のバージョンでは完全に無視されます。 または選択した内部スレッドに常に使用される明示的なスタック サイズを指定して置換可能性があります。  
  
 この構成要素、信頼性が低下より小さい仮想メモリの使用を要求が受け入れられる場合スタック サイズが小さくなる可能性があるため可能性のあるスタックを指定することは、多くの場合オーバーフローします。  
  
## <a name="example"></a>例  
 次の例では、CLR の使用の明示的なスタックのサイズが内部的に使用するスレッドを特定のことを要求する方法を示します。  
  
```xml  
<configuration>  
   <runtime>  
      <UseSmallInternalThreadStacks enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- [ランタイム設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)
