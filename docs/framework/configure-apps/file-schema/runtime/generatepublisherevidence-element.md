---
title: <generatePublisherEvidence> 要素
ms.date: 03/30/2017
helpviewer_keywords:
- generatePublisherEvidence element
- <generatePublisherEvidence> element
ms.assetid: 7d208f50-e8d5-4a42-bc1a-1cf3590706a8
ms.openlocfilehash: c2ba4a7244b7849e28eac38fb34a2cdd0d1f1048
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645355"
---
# <a name="generatepublisherevidence-element"></a>\<generatePublisherEvidence> 要素
ランタイムがコード アクセス<xref:System.Security.Policy.Publisher>セキュリティ (CAS) の証拠を作成するかどうかを指定します。  
  
[**\<構成>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<ランタイム>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<>を生成する**  
  
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
|`false`|証拠を作成<xref:System.Security.Policy.Publisher>しません。|  
|`true`|証拠<xref:System.Security.Policy.Publisher>を作成します。 これは既定値です。|  
  
### <a name="child-elements"></a>子要素  
 [なし] :  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|ランタイム初期化オプションに関する情報を含んでいます。|  
  
## <a name="remarks"></a>解説  
  
> [!NOTE]
> NET Framework 4 以降では、この要素はアセンブリの読み込み時間には影響しません。 詳細については、『セキュリティの[変更](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes)』の「セキュリティ ポリシーの簡略化」を参照してください。  
  
 共通言語ランタイム (CLR) は、読み込み時に Authenticode<xref:System.Security.Policy.Publisher>署名を検証して、アセンブリの証拠を作成しようとします。 ただし、既定では、ほとんどのアプリケーションは証拠を<xref:System.Security.Policy.Publisher>必要としません。 標準の CAS ポリシーは、<xref:System.Security.Policy.PublisherMembershipCondition>に依存しません。 アプリケーションがカスタム CAS ポリシーを使用してコンピューターで実行される場合、または部分的に信頼された環境で要求を満たす場合を除き、発行者の<xref:System.Security.Permissions.PublisherIdentityPermission>署名の検証に伴う不要な起動コストを回避する必要があります。 (ID アクセス許可の要求は、常に完全信頼環境で成功します)。  
  
> [!NOTE]
> サービスでは、スタートアップ の`<generatePublisherEvidence>`パフォーマンスを向上させるために、この要素を使用することをお勧めします。  この要素を使用すると、タイムアウトやサービスの起動のキャンセルを引き起こす遅延を回避することもできます。  
  
## <a name="configuration-file"></a>構成ファイル  
 この要素は、アプリケーション構成ファイルでのみ使用できます。  
  
## <a name="example"></a>例  
 次の例は、アプリケーションの`<generatePublisherEvidence>`CAS 発行者ポリシーのチェックを無効にする要素を使用する方法を示しています。  
  
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
