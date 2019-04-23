---
ms.openlocfilehash: 38c774417fc94fa080bf2b82c04d575e9068cdcb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59234176"
---
### <a name="reflection-objects-can-no-longer-be-passed-from-managed-code-to-out-of-process-dcom-clients"></a>リフレクション オブジェクトが、マネージド コードからアウト プロセス DCOM クライアントに渡されなくなった

|   |   |
|---|---|
|説明|リフレクション オブジェクトはマネージド コードからアウト プロセス DCOM クライアントに渡されなくなりました。 影響を受ける型は次のとおりです。<ul><li><xref:System.Reflection.Assembly?displayProperty=name></li><li><xref:System.Reflection.MemberInfo?displayProperty=name> (およびその派生型、<xref:System.Reflection.FieldInfo?displayProperty=name>、<xref:System.Reflection.MethodInfo?displayProperty=name>、<xref:System.Type?displayProperty=name>、<xref:System.Reflection.TypeInfo?displayProperty=name> など)</li><li><xref:System.Reflection.MethodBody?displayProperty=name></li><li><xref:System.Reflection.Module?displayProperty=name></li><li><xref:System.Reflection.ParameterInfo?displayProperty=name>。</li></ul>オブジェクトの <code>IMarshal</code> の呼び出しは <code>E_NOINTERFACE</code> を返します。|
|提案される解決策|非リフレクション オブジェクトで動作するように、マーシャリング コードを更新します。|
|スコープ|マイナー|
|Version|4.6|
|型|ランタイム|
