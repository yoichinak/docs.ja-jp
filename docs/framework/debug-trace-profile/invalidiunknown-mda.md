---
title: invalidIUnknown MDA
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid IUnknown pointer
- InvalidIUnknown MDA
- invalid IUnknown pointers
- IUnknown pointers
- managed debugging assistants (MDAs), invalid IUnknown pointer
ms.assetid: c7924771-a16b-40fe-b337-ce51dcdf6a12
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ea7f48ab61c16cb0430717074f1b1feab4827763
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052590"
---
# <a name="invalidiunknown-mda"></a>invalidIUnknown MDA
`invalidIUnknown` マネージド デバッグ アシスタント (MDA: Managed Debugging Assistant) は、無効な `IUnknown` ポインターがネイティブ コードからマネージド コードに渡されるとアクティブ化されます。 `IUnknown` インターフェイスが照会されたときに、`IUnknown` は、成功したことを返すことができませんでした。  
  
## <a name="symptoms"></a>症状  
 引数のマーシャリング中に COM インターフェイス ポインターをマーシャリングすると、予期しないエラーが発生します。  
  
## <a name="cause"></a>原因  
 CLR に渡された COM インターフェイスで、`QueryInterface` の実装が正しくありません。  
  
## <a name="resolution"></a>解決策  
 `QueryInterface` の実装を修正します。  
  
## <a name="effect-on-the-runtime"></a>ランタイムへの影響  
 この MDA は CLR に影響しません。  
  
## <a name="output"></a>出力  
 エラーの説明です。  
  
## <a name="configuration"></a>構成  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidIUnknown />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [マネージド デバッグ アシスタントによるエラーの診断](diagnosing-errors-with-managed-debugging-assistants.md)
- [相互運用マーシャリング](../interop/interop-marshaling.md)
