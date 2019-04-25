---
title: '軽減策: XML スキーマ検証'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b73dd4f4-f2dc-47a2-9425-3896e92321fb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e5c0087412a53177a7c43df838266f6d896c1bd9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59220475"
---
# <a name="mitigation-xml-schema-validation"></a>軽減策: XML スキーマ検証
[!INCLUDE[net_v46](../../../includes/net-v46-md.md)] 以降では、複合キーが使用され、1 つのキーが空の場合、XSD スキーマ検証で一意制約の違反が検出されます。  
  
## <a name="impact"></a>影響  
 この変更の影響は最小限のものになります。スキーマの仕様に基づき、複合キーが空のキーと共に使用されて `xsd:unique` の違反が発生した場合、スキーマの検証エラーの発生が予期されます。  
  
## <a name="mitigation"></a>軽減策  
 複合キーに空の 1 つのキーがある場合にスキーマ検証エラーが検出されるようにするかどうかは、構成可能な機能です。  
  
-   [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] 以降を対象とするアプリでは、スキーマ検証エラーの検出は既定で有効になっています。ただし、この動作を無効にして、スキーマ検証エラーが検出されないようにすることも可能です。  
  
-   [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] の下で実行されているものの、[!INCLUDE[net_v452](../../../includes/net-v452-md.md)] 以前のバージョンを対象とするアプリでは、既定ではスキーマ検証エラーが検出されません。ただし、この動作を有効にして、スキーマ検証エラーが検出されるようにすることも可能です。  
  
 この動作は、<xref:System.AppContext> クラスを使用して `System.Xml.IgnoreEmptyKeySequences` スイッチの値を定義することにより構成できます。 スイッチの既定値が `false` (空のキー シーケンスが無視されない) であるため、[!INCLUDE[net_v46](../../../includes/net-v46-md.md)] を対象とするアプリは、以下のコードを使用してスイッチの値を `true` に設定することにより、その動作を無効にすることができます。  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#1)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#1)]  
  
 [!INCLUDE[net_v452](../../../includes/net-v452-md.md)] 以前のバージョンを対象とするアプリでは、スイッチの既定値が `true` (空のキー シーケンスが無視される) であるため、以下のコードを使用してスイッチの値を `false` に設定することにより、複合キーに空のキーがある場合にスキーマ検証エラーを生成させることが可能です。  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#2)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#2)]  
  
## <a name="see-also"></a>関連項目

- [変更の再ターゲット](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
