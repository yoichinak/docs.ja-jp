---
title: パフォーマンス カウンターとインプロセス side-by-side アプリケーション
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- performance counters
- performance counters,and in-process side-by-side applications
- performance,.NET Framework applications
- performance monitoring,counters
ms.assetid: 6888f9be-c65b-4b03-a07b-df7ebdee2436
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c50132be2755119b19e38d94919eb4b0ab28d994
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64614321"
---
# <a name="performance-counters-and-in-process-side-by-side-applications"></a>パフォーマンス カウンターとインプロセス side-by-side アプリケーション
パフォーマンス モニター (Perfmon.exe) を使用すると、ランタイムごとにパフォーマンス カウンターを区別できるようになります。 このトピックでは、この機能を有効にするために必要なレジストリの変更について説明します。  
  
## <a name="the-default-behavior"></a>既定の動作  
 パフォーマンス モニターの既定では、アプリケーションごとにパフォーマンス カウンターが表示されますが、 これが問題になるシナリオが 2 つあります。  
  
- 同じ名前の 2 つのアプリケーションを監視する場合。 たとえば、両方の名前が myapp.exe の場合、**[インスタンス]** 列に一方のアプリケーションは **myapp**、もう一方は **myapp#1** と表示されます。 このような場合、特定のアプリケーションにパフォーマンス カウンターを対応付けることは困難です。 **myapp#1** 用に収集されたデータが 1 つ目の myapp.exe と 2 つ目の myapp.exe のどちらを示しているかが明確ではありません。  
  
- 1 つのアプリケーションが複数インスタンスの共通言語ランタイムを使用している場合。 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] は、インプロセスの side-by-side ホスティング シナリオをサポートしています。つまり、単一のプロセスまたはアプリケーションが複数インスタンスの共通言語ランタイムを読み込むことができます。 myapp.exe という単一のアプリケーションが 2 つのランタイム インスタンスを読み込むと、既定で、**[インスタンス]** 列に **myapp** および **myapp#1** と表示されます。 この場合、**myapp** と **myapp#1** が同じ名前の 2 つのアプリケーションを示しているか、2 つのランタイムを持つ単一のアプリケーションを示しているかが明確ではありません。 同じ名前の複数のアプリケーションが複数のランタイムを読み込む場合、あいまいさはさらに大きくなります。  
  
 このあいまいさを排除するために、レジストリ キーを設定できます。 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] を使用して開発したアプリケーションの場合、このようにレジストリを変更すると、**[インスタンス]** 列のアプリケーション名にプロセス識別子とランタイム インスタンス識別子が追加されます。 **[インスタンス]** 列に、*application* や *application*#1 ではなく、*application*_`p`*processID*\_`r`*runtimeID* と表示され、識別できるようになります。 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] がインストールされている場合、旧バージョンの共通言語ランタイム使用して開発されたアプリケーションのインスタンスは、*application\_*`p`*processID* と表されます。  
  
## <a name="performance-counters-for-in-process-side-by-side-applications"></a>インプロセス side-by-side アプリケーションのパフォーマンス カウンター  
 単一のアプリケーションでホストされている複数の共通言語ランタイム バージョンのパフォーマンス カウンターを処理するには、次の表のように 1 つのレジストリ キー設定を変更する必要があります。  
  
|||  
|-|-|  
|キー名|HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\\.NETFramework\Performance|  
|値の名前|ProcessNameFormat|  
|値の種類|REG_DWORD|  
|[値]|1 (0x00000001)|  
  
 `ProcessNameFormat` の値 0 は、既定の動作が有効であることを示します。つまり、Perfmon.exe には、アプリケーションごとのパフォーマンス カウンターが表示されます。 この値を 1 に設定すると、Perfmon.exe で複数バージョンのアプリケーションのあいまいさが解消され、ランタイムごとにパフォーマンス カウンターが表示されます。 `ProcessNameFormat` レジストリ キー設定の他の値はサポートされておらず、将来使用するために予約されています。  
  
 `ProcessNameFormat` レジストリ キー設定を更新した後は、新しいインスタンスの名前付け機能が正しく動作するように、Perfmon.exe、またはパフォーマンス カウンターを使用している他のプログラムを再起動する必要があります。  
  
 `ProcessNameFormat` 値をプログラムで変更する例を次に示します。  
  
 [!code-csharp[Conceptual.PerfCounters.InProSxS#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.perfcounters.inprosxs/cs/regsetting1.cs#1)]
 [!code-vb[Conceptual.PerfCounters.InProSxS#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.perfcounters.inprosxs/vb/regsetting1.vb#1)]  
  
 このようにレジストリを変更すると、Perfmon.exe では、[!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] をターゲットとするアプリケーション名は *application*_`p`*processID*\_`r`*runtimeID* と表示されます。この *application* はアプリケーション名、*processID* はアプリケーションのプロセス識別子、*runtimeID* は共通言語ランタイム識別子です。 たとえば、myapp.exe というアプリケーションが 2 インスタンスの共通言語ランタイムを読み込んだ場合、Perfmon.exe では、1 つ目のインスタンスは myapp_p1416_r10、2 つ目のインスタンスは myapp_p3160_r10 と識別できます。 ランタイム識別子は、プロセス内のランタイムのあいまいさを排除するだけです。ランタイムに関するその他の情報は提供されません (たとえば、ランタイム ID はランタイムのバージョンや SKU と関係がありません)。  
  
 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] がインストールされている場合、レジストリの変更は、旧バージョンの .NET Framework を使用して開発されたアプリケーションにも影響があります。 この場合、Perfmon.exe では *application_*`p`*processID* と表示されます。この *application* はアプリケーション名、*processID* はプロセス識別子です。 たとえば、myapp.exe という 2 つのアプリケーションのパフォーマンス カウンターを監視する場合、一方は myapp_p23900、もう一方は myapp_p24908 と表示される可能性があります。  
  
> [!NOTE]
>  プロセス識別子によって、旧バージョンのランタイムを使用する同じ名前の 2 つのアプリケーションが解決する際のあいまいさが排除されます。 旧バージョンの共通言語ランタイムは side-by-side シナリオをサポートしていないため、旧バージョンでランタイム識別子は必須ではありません。  
  
 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] が存在しない場合、またはアンインストールされた場合、このレジストリ キーを設定しても影響はありません。 つまり、同じ名前のアプリケーションが 2 つあっても、Perfmon.exe で *application*、*application#1* と表示されます (たとえば、**myapp** と **myapp#1**)。
