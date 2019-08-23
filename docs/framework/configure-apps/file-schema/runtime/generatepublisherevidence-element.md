---
title: <generatePublisherEvidence> 要素
ms.date: 03/30/2017
helpviewer_keywords:
- generatePublisherEvidence element
- <generatePublisherEvidence> element
ms.assetid: 7d208f50-e8d5-4a42-bc1a-1cf3590706a8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a5314fe5927abf2d3855acb45c763507ab6cb3c8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920748"
---
# <a name="generatepublisherevidence-element"></a>\<generatePublisherEvidence > 要素
ランタイムがコードアクセスセキュリティ<xref:System.Security.Policy.Publisher> (CAS) の証拠を作成するかどうかを指定します。  
  
 \<configuration>  
\<ランタイム >  
\<generatePublisherEvidence >  
  
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
|`enabled`|必須の属性です。<br /><br /> ランタイムが証拠を作成<xref:System.Security.Policy.Publisher>するかどうかを指定します。|  
  
## <a name="enabled-attribute"></a>enabled 属性  
  
|値|説明|  
|-----------|-----------------|  
|`false`|は証拠を<xref:System.Security.Policy.Publisher>作成しません。|  
|`true`|証拠<xref:System.Security.Policy.Publisher>を作成します。 既定値です。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|ランタイム初期化オプションに関する情報を含んでいます。|  
  
## <a name="remarks"></a>Remarks  
  
> [!NOTE]
> .NET Framework 4 以降では、この要素はアセンブリの読み込み時間に影響しません。 詳細については、「セキュリティの[変更](../../../security/security-changes.md)」の「セキュリティポリシーの簡略化」を参照してください。  
  
 共通言語ランタイム (CLR) は、読み込み時に Authenticode 署名を検証して、 <xref:System.Security.Policy.Publisher>アセンブリの証拠を作成しようとします。 ただし、既定では、ほとんどのアプリケーションは<xref:System.Security.Policy.Publisher>証拠を必要としません。 標準の CAS ポリシーは、 <xref:System.Security.Policy.PublisherMembershipCondition>に依存しません。 カスタム CAS ポリシーを使用しているコンピューターでアプリケーションを実行する場合や、部分信頼環境での<xref:System.Security.Permissions.PublisherIdentityPermission>要求を満たす場合を除き、発行元の署名の検証に関連する不要な起動コストを回避する必要があります。 (Id 権限の要求は、完全に信頼された環境では常に成功します)。  
  
> [!NOTE]
> サービスでは、 `<generatePublisherEvidence>`要素を使用して起動時のパフォーマンスを向上させることをお勧めします。  また、この要素を使用すると、タイムアウトを発生させたり、サービスの開始をキャンセルしたりする可能性がある遅延を回避することもできます。  
  
## <a name="configuration-file"></a>構成ファイル  
 この要素は、アプリケーション構成ファイルでのみ使用できます。  
  
## <a name="example"></a>例  
 次の例は、要素を使用`<generatePublisherEvidence>`して、アプリケーションの CAS 発行者ポリシーのチェックを無効にする方法を示しています。  
  
```xml  
<configuration>  
    <runtime>  
        <generatePublisherEvidence enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- [ランタイム設定スキーマ](index.md)
- [構成ファイル スキーマ](../index.md)
