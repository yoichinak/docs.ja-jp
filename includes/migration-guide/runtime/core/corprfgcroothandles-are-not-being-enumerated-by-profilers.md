---
ms.openlocfilehash: 8dc98b2d9c2c0b5f145ebce48cf8f5e054975c6e
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858572"
---
### <a name="corprfgcroothandles-are-not-being-enumerated-by-profilers"></a>COR_PRF_GC_ROOT_HANDLE がプロファイラーで列挙されていない

|   |   |
|---|---|
|説明|.NET Framework v4.5.1 では、プロファイル API <code>RootReferences2()</code> が正しく <code>COR_PRF_GC_ROOT_HANDLE</code> を返しません (代わりに、<code>COR_PRF_GC_ROOT_OTHER</code> として返される)。 この問題は、.NET Framework 4.6 以降で修正されています。|
|提案される解決策|この問題は .NET Framework 4.6 で修正されたため、このバージョンの .NET Framework にアップグレードすることによって対処できます。|
|スコープ|マイナー|
|Version|4.5.1|
|型|ランタイム|

