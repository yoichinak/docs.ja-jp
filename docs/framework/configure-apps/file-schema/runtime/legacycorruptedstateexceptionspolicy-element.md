---
title: <legacyCorruptedStateExceptionsPolicy> 要素
ms.date: 03/30/2017
helpviewer_keywords:
- <legacyCorruptedStateExceptionsPolicy> element
- legacyCorruptedStateExceptionsPolicy element
ms.assetid: e0a55ddc-bfa8-4f3e-ac14-d1fc3330e4bb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d8733e11aba30ebea30fc71a5350f76dfd041eb4
ms.sourcegitcommit: 518e7634b86d3980ec7da5f8c308cc1054daedb7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/01/2019
ms.locfileid: "66456406"
---
# <a name="legacycorruptedstateexceptionspolicy-element"></a>\<legacyCorruptedStateExceptionsPolicy > 要素
共通言語ランタイムがアクセス違反およびその他の破損状態例外をキャッチするマネージ コードをできるかどうかを指定します。  
  
 \<configuration>  
\<runtime>  
\<legacyCorruptedStateExceptionsPolicy>  
  
## <a name="syntax"></a>構文  
  
```xml  
<legacyCorruptedStateExceptionsPolicy enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`enabled`|必須の属性です。<br /><br /> アプリケーションをキャッチすることを指定します。 アクセス違反などの例外エラーの状態が破損します。|  
  
## <a name="enabled-attribute"></a>enabled 属性  
  
|値|説明|  
|-----------|-----------------|  
|`false`|アプリケーションはキャッチできない破損状態例外のエラーへのアクセス違反など。 既定値です。|  
|`true`|アプリケーションがキャッチ破損状態例外のエラーへのアクセス違反など。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。|  
  
## <a name="remarks"></a>Remarks  
 .NET Framework 3.5 およびそれ以前のバージョンでは、共通言語ランタイムは、破損したプロセス状態で発生した例外をキャッチするマネージ コードを使用できます。 アクセス違反は、この種類の例外の例を示します。  
  
 以降では、 [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]、マネージ コードではこれらの種類の例外のキャッチされなく`catch`ブロックします。 ただし、この変更を上書きし、2 つの方法で破損状態例外の処理を維持できます。  
  
- 設定、`<legacyCorruptedStateExceptionsPolicy>`要素の`enabled`属性を`true`します。 この構成設定は適用されているプロセスであり、すべてのメソッドの影響します。  
  
 - または -  
  
- 適用、<xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType>属性をメソッド、例外を含む`catch`ブロックします。  
  
 この構成要素は、以降、.NET Framework 4 でのみ使用できます。  
  
## <a name="example"></a>例  
 次の例では、アプリケーションが .NET Framework 4 では前に、の動作に戻すし、すべての破損状態例外のエラーをキャッチする必要がありますを指定する方法を示します。  
  
```xml  
<configuration>  
   <runtime>  
      <legacyCorruptedStateExceptionsPolicy enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>
- [ランタイム設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)
