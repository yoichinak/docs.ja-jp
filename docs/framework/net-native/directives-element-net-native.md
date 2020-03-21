---
title: <Directives>要素 (.NET ネイティブ)
ms.date: 03/30/2017
ms.assetid: 444846f3-48d5-4341-a43e-69f7221389eb
ms.openlocfilehash: 49c1aaf005b80a6c1c1fa382eebc2cb0dbfa4be7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181055"
---
# <a name="directives-element-net-native"></a>\<要素 (.NET ネイティブ)>ディレクティブ
NET ネイティブのすべてのランタイム ディレクティブ ファイルのルート要素。  
  
 `<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">`
  
## <a name="syntax"></a>構文  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <!-- child elements -->
</Directives>  
```  
  
## <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`xmlns`|XML 名前空間。 その値は常に **" "http://schemas.microsoft.com/netfx/2013/01/metadataです**。|  
  
## <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<アプリケーション>](application-element-net-native.md)|リフレクションで使用可能なメタデータを持つアプリケーション全体の型と型のメンバーのコンテナーとして機能します。|  
|[\<図書館>](library-element-net-native.md)|実行時にメタデータを必要とする子型と型のメンバーを持つアセンブリを定義します。|  
  
## <a name="remarks"></a>解説  
 各ランタイム ディレクティブ ファイルには、`<Directives>` 要素を 1 つのみ含めることができます。  
  
 要素`<Directives>`には、0 個または 1 つの[\<アプリケーション>](application-element-net-native.md)要素、および 0、1 つ、または複数の[\<ライブラリ>](library-element-net-native.md)要素を含めることができます。  
  
## <a name="see-also"></a>関連項目

- [ランタイム ディレクティブ (rd.xml) 構成ファイル リファレン](runtime-directives-rd-xml-configuration-file-reference.md)
- [ランタイム ディレクティブ要素](runtime-directive-elements.md)
