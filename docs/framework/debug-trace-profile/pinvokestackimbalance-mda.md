---
title: pInvokeStackImbalance MDA
ms.date: 03/30/2017
helpviewer_keywords:
- signatures, platform invoke
- stack depth
- platform invoke stack imbalance
- MDAs (managed debugging assistants), platform invoke
- platform invoke, run-time errors
- PInvokeStackImbalance MDA
- managed debugging assistants (MDAs), platform invoke
ms.assetid: 34ddc6bd-1675-4f35-86aa-de1645d5c631
author: mairaw
ms.author: mairaw
ms.openlocfilehash: dc4a48c79fc39b12f8231bd913b4ca8970c0f46f
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052364"
---
# <a name="pinvokestackimbalance-mda"></a>PInvokeStackImbalance MDA

マネージデバッグアシスタント (MDA) は、プラットフォーム呼び出しの後のスタックの深さが、予想されるスタックの深さと一致しないことを CLR が検出したときに<xref:System.Runtime.InteropServices.DllImportAttribute>アクティブ化されます。これには、属性で指定した呼び出し規約と、 `PInvokeStackImbalance`マネージシグネチャ内のパラメーターの宣言。

`PInvokeStackImbalance` MDA は 32 ビット x86 プラットフォームに対してのみ実装されています。

> [!NOTE]
> MDA `PInvokeStackImbalance`は、既定では無効になっています。 Visual Studio 2017 では、 `PInvokeStackImbalance` **[例外設定]** ダイアログボックスの **[マネージデバッグアシスタント]** の一覧に MDA が表示されます > ([**Windows**  >  **のデバッグ] を選択すると表示されます)。例外設定**)。 ただし、[スローされ**たときに中断**する] チェックボックスをオンまたはオフにしても、MDA は有効または無効になりません。MDA がアクティブになったときに Visual Studio が例外をスローするかどうかのみを制御します。

## <a name="symptoms"></a>症状

プラットフォーム呼び出しの実行時または実行後に、アプリケーションでアクセス違反またはメモリ破損が発生します。

## <a name="cause"></a>原因

プラットフォーム呼び出しのマネージド シグネチャが、呼び出されているメソッドのアンマネージド シグネチャと一致しない可能性があります。  この不一致は、正しい数のパラメーターを宣言しないか、適切なサイズのパラメーターを指定しないマネージド シグネチャで発生する可能性があります。  また、<xref:System.Runtime.InteropServices.DllImportAttribute> 属性によって指定されている可能性がある呼び出し規則が、アンマネージ呼び出し規則と一致しない場合にも、MDA がアクティブ化される可能性があります。

## <a name="resolution"></a>解決策

マネージド プラットフォーム呼び出しシグネチャ、および呼び出し規則を確認して、ネイティブ ターゲットのシグネチャと呼び出し規則に一致することを確認します。  マネージド側とアンマネージド側の両方で、呼び出し規則を明示的に指定してください。 また、あまり可能性はありませんが、アンマネージ コンパイラのバグなど、何らかの理由によりアンマネージ関数でスタックの不均衡が発生している場合もあります。

## <a name="effect-on-the-runtime"></a>ランタイムへの影響

すべてのプラットフォーム呼び出しが、CLR の最適化されていないパスを取得するよう強制します。

## <a name="output"></a>出力

MDA メッセージが、スタックの不均衡の原因であるプラットフォーム呼び出しメソッド呼び出しの名前を示します。 メソッド `SampleMethod` のプラットフォーム呼び出しのサンプル メッセージは、次のとおりです。

**PInvoke 関数 ' SampleMethod ' の呼び出しがスタックを不均衡にしました。マネージ PInvoke 署名がアンマネージターゲットシグネチャと一致しないことが原因である可能性があります。PInvoke 署名の呼び出し規約とパラメーターが、ターゲットのアンマネージシグネチャと一致することを確認します。**

## <a name="configuration"></a>構成

```xml
<mdaConfig>
  <assistants>
    <pInvokeStackImbalance />
  </assistants>
</mdaConfig>
```

## <a name="see-also"></a>関連項目

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [マネージド デバッグ アシスタントによるエラーの診断](diagnosing-errors-with-managed-debugging-assistants.md)
- [相互運用マーシャリング](../interop/interop-marshaling.md)
