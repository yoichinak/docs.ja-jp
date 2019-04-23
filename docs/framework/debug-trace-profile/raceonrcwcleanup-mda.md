---
title: raceOnRCWCleanup MDA
ms.date: 03/30/2017
helpviewer_keywords:
- RCW
- managed debugging assistants (MDAs), RCWs
- race on RCW cleanup
- MDAs (managed debugging assistants), RCWs
- RaceOnRCWCleanup MDA
- runtime callable wrappers
ms.assetid: bee1e9b1-50a8-4c89-9cd9-7dd6b2458187
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 628790bb8229dc519589c122235f07a38ba57c1c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59100237"
---
# <a name="raceonrcwcleanup-mda"></a>raceOnRCWCleanup MDA
<xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType> メソッドなどのコマンドを使用して [ランタイム呼び出し可能ラッパー](../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW: Runtime Callable Wrapper) を解放する呼び出しがなされた時点でその RCW が使用中であることを共通言語ランタイム (CLR: Common Language Runtime) が検出すると、`raceOnRCWCleanup` マネージド デバッグ アシスタント (MDA: Managed Debugging Assistant) がアクティブ化されます。  
  
## <a name="symptoms"></a>症状  
 <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> メソッド、または類似メソッドを使用して RCW が解放中または解放後に、アクセス違反またはメモリ破損が発生します。  
  
## <a name="cause"></a>原因  
 別のスレッドまたは解放中のスレッド スタックで、RCW が使用中です。  使用中の RCW は解放できません。  
  
## <a name="resolution"></a>解像度  
 現在のスレッドまたは他のスレッドで使用中の可能性がある RCW は、解放しないでください。  
  
## <a name="effect-on-the-runtime"></a>ランタイムへの影響  
 この MDA は CLR に影響しません。  
  
## <a name="output"></a>出力  
 エラーを説明するメッセージです。  
  
## <a name="configuration"></a>構成  
  
```xml  
<mdaConfig>  
  <assistants>  
    <raceOnRCWCleanup/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [マネージド デバッグ アシスタントによるエラーの診断](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [相互運用マーシャリング](../../../docs/framework/interop/interop-marshaling.md)
