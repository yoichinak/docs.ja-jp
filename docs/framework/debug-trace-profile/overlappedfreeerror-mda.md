---
title: overlappedFreeError MDA
ms.date: 03/30/2017
helpviewer_keywords:
- OverlappedFreeError MDA
- overlapped free method call error
- managed debugging assistants (MDAs), overlapped structures
- overlapped structures
- MDAs (managed debugging assistants), overlapped structures
- freeing overlapped structures
ms.assetid: b6ab2d48-6eee-4bab-97a3-046b3b0a5470
author: mairaw
ms.author: mairaw
ms.openlocfilehash: defd7f90fcac8d1e98104796682058638c9bd799
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59127076"
---
# <a name="overlappedfreeerror-mda"></a>overlappedFreeError MDA
オーバーラップされた操作が完了する前に <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29?displayProperty=nameWithType> メソッドが呼び出されると、`overlappedFreeError` マネージド デバッグ アシスタント (MDA) がアクティブになります。  
  
## <a name="symptoms"></a>症状  
 アクセス違反またはガベージ コレクションされたヒープの破損。  
  
## <a name="cause"></a>原因  
 操作が完了する前に、オーバーラップされた構造が解放されました。 オーバーラップされたポインターを使用する関数は、解放された後に構造に書き込む可能性があります。 その場合、現時点で別のオブジェクトがその領域を占有していることによってヒープが破損する可能性があります。  
  
 オーバーラップされた操作が正常に起動しなかった場合、この MDA はエラーを発生しないことがあります。  
  
## <a name="resolution"></a>解像度  
 <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29> メソッドを呼び出す前に、オーバーラップされた構造を使用している I/O 操作が必ず完了するようにします。  
  
## <a name="effect-on-the-runtime"></a>ランタイムへの影響  
 この MDA は CLR に影響しません。  
  
## <a name="output"></a>出力  
 この MDA のサンプル出力を次に示します。  
  
 `An overlapped pointer (0x00ea3430) that was not allocated on the GC heap was passed via Pinvoke to the win32 function 'WriteFile' in module 'KERNEL32.DLL'. If the AppDomain is shut down, this can cause heap corruption when the async I/O completes. The best solution is to pass a NativeOverlappedStructure retrieved from a call to System.Threading.Overlapped.Pack(). If the AppDomain exits, the CLR will keep this structure alive and pinned until the I/O completes.`  
  
## <a name="configuration"></a>構成  
  
```xml  
<mdaConfig>  
  <assistants>  
    <overlappedFreeError/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [マネージド デバッグ アシスタントによるエラーの診断](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [相互運用マーシャリング](../../../docs/framework/interop/interop-marshaling.md)
