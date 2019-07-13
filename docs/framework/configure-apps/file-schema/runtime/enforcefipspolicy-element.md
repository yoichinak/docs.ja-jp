---
title: <enforceFIPSPolicy> 要素
ms.date: 03/30/2017
helpviewer_keywords:
- enforceFIPSPolicy element
- FIPS
- <enforceFIPSPolicy> element
- Federal Information Processing Standards (FIPS)
ms.assetid: c35509c4-35cf-43c0-bb47-75e4208aa24e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c13dd2f00e08539d2ba502058c74aa4a1525e3ff
ms.sourcegitcommit: 5ae6affa0b171be3bb5f4729fb68ea4fe799f959
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/10/2019
ms.locfileid: "66816111"
---
# <a name="enforcefipspolicy-element"></a>\<enforceFIPSPolicy > 要素
暗号化アルゴリズムが連邦情報処理規格 (FIPS: Federal Information Processing Standard) に準拠する必要があるコンピューターの構成要件を強制するかどうかを指定します。  
  
 \<configuration> 要素  
\<runtime> 要素  
\<enforceFIPSPolicy > 要素  
  
## <a name="syntax"></a>構文  
  
```xml  
<enforceFIPSPolicy enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|enabled|必須の属性です。<br /><br /> 暗号化アルゴリズムは FIPS 準拠でなければならないこと、コンピューターの構成要件の強制を有効にするかどうかを指定します。|  
  
## <a name="enabled-attribute"></a>enabled 属性  
  
|値|説明|  
|-----------|-----------------|  
|`true`|FIPS に準拠する暗号アルゴリズムを要求するように、コンピューターを構成する場合は、その要件が適用されます。 クラスは、コンス トラクターは、FIPS 準拠アルゴリズムを実装している場合または`Create`そのコンピューターで実行された場合、そのクラスのメソッドが例外をスローします。 既定値です。|  
|`false`|アプリケーションで使用される暗号化アルゴリズムは、コンピューターの構成に関係なく、FIPS に準拠する必要はありません。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。|  
  
## <a name="remarks"></a>Remarks  
 以降、.NET Framework 2.0 では、暗号アルゴリズムを実装するクラスの作成は、コンピューターの構成によって制御されます。 FIPS に準拠するアルゴリズムを要求するように、コンピューターが構成されているクラスは、FIPS 準拠アルゴリズムを実装する場合は、そのクラスのインスタンスを作成しようとするとは、例外をスローします。 コンス トラクターがスロー、<xref:System.InvalidOperationException>例外、および`Create`メソッドでスロー、<xref:System.Reflection.TargetInvocationException>と内部例外<xref:System.InvalidOperationException>例外。  
  
 構成は、fips コンプライアンスを必要とするコンピューターでアプリケーションを実行し、アプリケーションでは fips 準拠アルゴリズムを使用することができます要素を使用してこの構成ファイルから共通言語ランタイム (CLR) を防ぐためにFIPS 準拠を適用します。 この要素は、.NET Framework 2.0 Service Pack 1 で導入されました。  
  
## <a name="example"></a>例  
 次の例では、CLR が FIPS 準拠を適用することを防止する方法を示します。  
  
```xml  
<configuration>  
    <runtime>  
        <enforceFIPSPolicy enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- [ランタイム設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [暗号モデル](../../../../../docs/standard/security/cryptography-model.md)
