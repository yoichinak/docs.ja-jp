---
title: <generatePublisherEvidence> 要素
ms.date: 03/30/2017
helpviewer_keywords:
- generatePublisherEvidence element
- <generatePublisherEvidence> element
ms.assetid: 7d208f50-e8d5-4a42-bc1a-1cf3590706a8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 09a12f062b2fe3ad6e5ac90f0d268bbbeab44876
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59198921"
---
# <a name="generatepublisherevidence-element"></a>\<generatePublisherEvidence > 要素
ランタイムを作成するかどうかを指定します。<xref:System.Security.Policy.Publisher>コード アクセス セキュリティ (CAS) のための証拠。  
  
 \<configuration>  
\<runtime>  
\<generatePublisherEvidence>  
  
## <a name="syntax"></a>構文  
  
```xml  
<generatePublisherEvidence    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`enabled`|必須の属性です。<br /><br /> ランタイムを作成するかどうかを指定します。<xref:System.Security.Policy.Publisher>証拠。|  
  
## <a name="enabled-attribute"></a>enabled 属性  
  
|値|説明|  
|-----------|-----------------|  
|`false`|作成されません<xref:System.Security.Policy.Publisher>証拠。|  
|`true`|作成<xref:System.Security.Policy.Publisher>証拠。 既定値です。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|ランタイム初期化オプションに関する情報を含んでいます。|  
  
## <a name="remarks"></a>Remarks  
  
> [!NOTE]
>  [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]なり、後でこの要素にはアセンブリの読み込み時間に効力はありません。 詳細については、「セキュリティ ポリシーの簡略化」のセクションを参照してください。[セキュリティ変更](../../../../../docs/framework/security/security-changes.md)します。  
  
 共通言語ランタイム (CLR) を作成する読み込み時に Authenticode 署名を検証しようとする<xref:System.Security.Policy.Publisher>アセンブリの証拠。 ただし、既定では、ほとんどのアプリケーションは必要ありません<xref:System.Security.Policy.Publisher>証拠。 標準の CAS ポリシーに依存せず、<xref:System.Security.Policy.PublisherMembershipCondition>します。 アプリケーションがカスタムの CAS ポリシーを使用しているコンピューター上で実行しますかのニーズを満たすにしない限り、発行元の署名の検証に関連付けられている不要なスタートアップ コストを回避する必要があります<xref:System.Security.Permissions.PublisherIdentityPermission>部分信頼環境でします。 (Id アクセス許可の要求は常には、完全に信頼された環境で失敗した)。  
  
> [!NOTE]
>  使用するサービスをお勧め、`<generatePublisherEvidence>`起動時のパフォーマンスを向上させるために要素。  この要素を使用しても、タイムアウトと、サービスのスタートアップのキャンセルを引き起こす可能性のある遅延を避けるためとことができます。  
  
## <a name="configuration-file"></a>構成ファイル  
 この要素は、アプリケーション構成ファイルでのみ使用できます。  
  
## <a name="example"></a>例  
 次の例は、使用する方法を示します、`<generatePublisherEvidence>`チェック アプリケーションの CA の発行元ポリシーを無効にする要素。  
  
```xml  
<configuration>  
    <runtime>  
        <generatePublisherEvidence enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- [ランタイム設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)
