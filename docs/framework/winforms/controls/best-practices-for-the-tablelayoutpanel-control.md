---
title: TableLayoutPanel コントロールの推奨される手順
ms.date: 03/30/2017
helpviewer_keywords:
- layout [Windows Forms]
- TableLayoutPanel control [Windows Forms], best practices
- forms [Windows Forms], best practices
- AutoSize property [Windows Forms], tableLayoutPanel control
- controls [Windows Forms], sizing
- TableLayoutPanel control [Windows Forms], AutoSize behavior
- layout [Windows Forms], AutoSize
- layout [Windows Forms], best practices
- best practices [Windows Forms], tableLayoutPanel control
- sizing [Windows Forms], automatic
- automatic sizing
ms.assetid: b6706efb-d7a4-45ec-8cf4-08fa993e3afb
ms.openlocfilehash: 57abf3527af146f1ce918bcabbc6a5a34bfb9b34
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59222329"
---
# <a name="best-practices-for-the-tablelayoutpanel-control"></a>TableLayoutPanel コントロールの推奨される手順
<xref:System.Windows.Forms.TableLayoutPanel>コントロールは、Windows フォームで使用する前に慎重に考慮すべき強力なレイアウト機能を提供します。  
  
## <a name="recommendations"></a>推奨事項  
 次の推奨事項では、使用するのに役立つ、<xref:System.Windows.Forms.TableLayoutPanel>最大限に活用するコントロール。  
  
### <a name="targeted-use"></a>対象の使用  
 使用して、<xref:System.Windows.Forms.TableLayoutPanel>慎重に制御します。 サイズ変更可能なレイアウトを必要とするすべての状況で使用する必要がありますできません。 次の一覧の使用を最大限に活用できるレイアウトの説明、<xref:System.Windows.Forms.TableLayoutPanel>コントロール。  
  
-   レイアウトでは、相互に比例してサイズが変更されるフォームの複数の部分があります。  
  
-   変更または追加または削除されるユーザーにカスタマイズ可能なフィールドがデータ エントリ フォームなどの実行時に動的に生成されるレイアウトは、基本設定に基づいています。  
  
-   全体の固定サイズのままにレイアウトします。 たとえば、ダイアログ ボックスが 800 x 600 未満にしておく必要がありますが、ローカライズされた文字列をサポートする必要があります。  
  
 次に示しますを大幅に利用しないレイアウト、<xref:System.Windows.Forms.TableLayoutPanel>コントロール。  
  
-   1 つの列のラベルとテキスト入力領域の 1 つの列のエントリのフォームが単純なデータ。  
  
-   1 つの大きなフォームには、サイズ変更が発生したときに使用可能なすべての領域の塗りつぶし領域が表示されます。 この例は、1 つを表示するフォーム<xref:System.Windows.Forms.PropertyGrid>コントロール。 この場合、アンカー、ために使用、フォームのサイズが変更されたときに他に何も展開する必要があります。  
  
 どのコントロールでは、必要がありますは慎重に選択、<xref:System.Windows.Forms.TableLayoutPanel>コントロール。 増加 30% がアンカーを使用して、文字列がある場合は、使用を検討して、<xref:System.Windows.Forms.Control.Anchor%2A>プロパティのみです。 場合は、レイアウトが必要な容量を見積もるを使用して<xref:System.Windows.Forms.Control.Dock%2A>と<xref:System.Windows.Forms.Control.Anchor%2A>が残りの領域の詳細を見積もるよりも簡単と<xref:System.Windows.Forms.Control.AutoSize%2A>動作します。  
  
 一般を使用してレイアウトを設計するときに、<xref:System.Windows.Forms.TableLayoutPanel>コントロールを設計をできるだけシンプルに保ちます。  
  
### <a name="use-the-document-outline-window"></a>ドキュメント アウトライン ウィンドウを使用します。  
 ドキュメント アウトライン ウィンドウでは、ツリー ビュー、レイアウト、コントロールの z オーダーと親子のリレーションシップの操作に使用することができます。 **ビュー メニュー**を選択します**その他の Windows**を選択し、**ドキュメント アウトライン**します。  
  
### <a name="avoid-nesting"></a>入れ子を回避します。  
 その他の入れ子を避ける<xref:System.Windows.Forms.TableLayoutPanel>内で制御を<xref:System.Windows.Forms.TableLayoutPanel>コントロール。 入れ子になったレイアウトのデバッグは困難なことができます。  
  
### <a name="avoid-visual-inheritance"></a>ビジュアル継承を回避します。  
 <xref:System.Windows.Forms.TableLayoutPanel>コントロールが、Windows フォーム デザイナーでビジュアル継承をサポートしていません。 A<xref:System.Windows.Forms.TableLayoutPanel>デザイン時に、「ロック」として、派生クラスでのコントロールが表示されます。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.TableLayoutPanel>
- <xref:System.Windows.Forms.FlowLayoutPanel>
