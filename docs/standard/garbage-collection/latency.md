---
title: 待機モード
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, intrusiveness
- garbage collection, latency modes
ms.assetid: 96278bb7-6eab-4612-8594-ceebfc887d81
ms.openlocfilehash: 8833c88c3221c0a375011eb62dd712340f7e89cd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120904"
---
# <a name="latency-modes"></a>待機モード
オブジェクトを再利用するには、ガベージ コレクターはアプリケーションで実行中のすべてのスレッドを停止する必要があります。 状況によっては、アプリケーションがデータの取得やコンテンツの表示を行うときなど、重要なときにフル ガベージ コレクションが発生し、パフォーマンスが低下することがあります。 ガベージ コレクターが作業に悪影響を与える度合いを調整するには、<xref:System.Runtime.GCSettings.LatencyMode%2A?displayProperty=nameWithType> プロパティを <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType> 値のいずれかに設定することができます。  
  
 Latency (待機時間) は、ガベージ コレクターが実行中のアプリケーションに割って入る時間を指します。 待機時間が短い場合、ガベージ コレクターがオブジェクトを再利用する処理は控えめになり、アプリケーションに悪影響を与える度合いが下がります。 <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType> 列挙体には、待機時間の短い設定として次の 2 つがあります。  
  
- <xref:System.Runtime.GCLatencyMode.LowLatency> では、ジェネレーション 2 のガベージ コレクションが停止し、ジェネレーション 0 および 1 のみガベージ コレクションが実行されます。 これは、短時間の場合にのみ使用できます。 この設定を長時間にわたって使用すると、システムのメモリが不足してガベージ コレクターがガベージ コレクションをトリガーした場合に、アプリケーションが少しの間停止したり、高速性を必要とする操作が中断されたりすることがあります。 この設定は、ワークステーションのガベージ コレクションでのみ使用できます。  
  
- <xref:System.Runtime.GCLatencyMode.SustainedLowLatency> では、フォアグラウンドのジェネレーション 2 のガベージ コレクションが停止し、ジェネレーション 0 および 1 とバックグラウンドのジェネレーション 2 のガベージ コレクションのみが実行されます。 これは長時間にわたって使用でき、ワークステーションとサーバーの両方のガベージ コレクションで使用できます。 この設定は、[同時実行ガベージ コレクション](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md)が無効の場合には使用できません。  
  
 待機時間の短い設定になっている場合でも、次の状況ではジェネレーション 2 のガベージ コレクションの停止が解除されます。  
  
- システムがオペレーティング システムからメモリ不足の通知を受け取った場合。  
  
- アプリケーション コードから <xref:System.GC.Collect%2A?displayProperty=nameWithType> メソッドを呼び出し、`generation` パラメーターに 2 を指定してガベージ コレクションを実行した場合。  
  
 次の表に、<xref:System.Runtime.GCLatencyMode> の各値を使用するアプリケーション シナリオを示します。  
  
|待機時間モード|アプリケーション シナリオ|  
|------------------|---------------------------|  
|<xref:System.Runtime.GCLatencyMode.Batch>|UI 操作のないアプリケーションの場合、またはサーバー側の操作の場合に使用します。<br /><br /> これは、[同時実行ガベージ コレクション](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md)が無効の場合の既定モードです。|  
|<xref:System.Runtime.GCLatencyMode.Interactive>|UI を持つほとんどのアプリケーションの場合に使用します。<br /><br /> これは、[同時実行ガベージ コレクション](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md)が有効の場合の既定モードです。|  
|<xref:System.Runtime.GCLatencyMode.LowLatency>|ガベージ コレクターからの割り込みにより重大な影響を受け、高速性を必要とする、短期間の操作を実行するアプリケーションの場合に使用します。 たとえば、アニメーションのレンダリングやデータの取得機能を実行するアプリケーションなどがあります。|  
|<xref:System.Runtime.GCLatencyMode.SustainedLowLatency>|ガベージ コレクターからの割り込みにより重大な影響を受け、高速性を必要とする、さほど処理時間を必要としないものの長時間になる可能性のある操作を実行するアプリケーションの場合に使用します。 たとえば、取引時間中に市場データの変化に応じて迅速な応答時間を必要とするアプリケーションなどがあります。<br /><br /> このモードでは、マネージド ヒープのサイズが他のモードより大きくなります。 マネージド ヒープは最適化されないため、断片化の割合が高くなる可能性があります。 十分なメモリが使用可能であることを確認してください。|  
  
## <a name="guidelines-for-using-low-latency"></a>待機時間の短いモードの使用に関するガイドライン  
 <xref:System.Runtime.GCLatencyMode.LowLatency> モードを使用する場合は、次のガイドラインを検討してください。  
  
- 待機時間を短くする期間は、できるだけ短くします。  
  
- 待機時間を短くする期間中は、大量のメモリを割り当てないようにします。 ガベージ コレクションによって再利用されるオブジェクトの数が少なくなるため、メモリ不足の通知が発生する可能性があります。  
  
- 待機時間の短いモードの間は、割り当ての数、特に大きなオブジェクト ヒープや固定されたオブジェクトへの割り当ての数を最小限に抑えます。  
  
- 割り当てられる可能性のあるスレッドに注意します。 <xref:System.Runtime.GCSettings.LatencyMode%2A> プロパティの設定はプロセス全体に適用されるため、割り当てられた他のスレッドで <xref:System.OutOfMemoryException> が発生する可能性があります。  
  
- 待機時間の短いコードを制約された実行領域にラップします (詳細については、「[制約された実行領域](../../../docs/framework/performance/constrained-execution-regions.md)」を参照してください)。  
  
- 待機時間を短くする期間中でも、<xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%29?displayProperty=nameWithType> メソッドを呼び出せばジェネレーション 2 のガベージ コレクションを強制できます。  
  
## <a name="see-also"></a>関連項目

- <xref:System.GC?displayProperty=nameWithType>
- [発生したコレクション](../../../docs/standard/garbage-collection/induced.md)
- [ガベージ コレクション](../../../docs/standard/garbage-collection/index.md)
