---
ms.openlocfilehash: 77e04333ed2b9a5ca8b900c1355fb5b12957772d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59774441"
---
### <a name="machinekeyencode-and-machinekeydecode-methods-are-now-obsolete"></a>MachineKey.Encode メソッドと MachineKey.Decode メソッドが廃止に

|   |   |
|---|---|
|説明|これらのメソッドは今後使用しません。 これらのメソッドを呼び出すコードをコンパイルすると、コンパイラ警告が生成されます。|
|提案される解決策|別の方法として、<xref:System.Web.Security.MachineKey.Protect(System.Byte[],System.String[])> および <xref:System.Web.Security.MachineKey.Unprotect(System.Byte[],System.String[])> を使用することをお勧めします。 または、ビルド警告を抑制するか、古いコンパイラを使用して警告を回避できます。 API は、まだサポートされています。|
|スコープ|マイナー|
|Version|4.5|
|型|再ターゲット中|
|影響を受ける API|<ul><li><xref:System.Web.Security.MachineKey.Encode(System.Byte[],System.Web.Security.MachineKeyProtection)?displayProperty=nameWithType></li><li><xref:System.Web.Security.MachineKey.Decode(System.String,System.Web.Security.MachineKeyProtection)?displayProperty=nameWithType></li></ul>|
