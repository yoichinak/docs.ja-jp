---
title: '方法: Freezable を読み取り専用にする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Freezable objects [WPF], making read-only
ms.assetid: 6c544b7d-d3c9-4736-aa90-4b8728234ccb
ms.openlocfilehash: 9b7102db4de0df7183355e50e3b372eac30d81b3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61771021"
---
# <a name="how-to-make-a-freezable-read-only"></a>方法: Freezable を読み取り専用にする
この例では、作成、<xref:System.Windows.Freezable>呼び出すことによって、読み取り専用の<xref:System.Windows.Freezable.Freeze%2A>メソッド。  
  
 固定することはできません、<xref:System.Windows.Freezable>オブジェクトのかどうかは、次の条件のいずれかが`true`オブジェクトについて。  
  
- アニメーション化されたまたは、データ バインドされたプロパティ。  
  
- 動的なリソースが設定されているプロパティがあります。 動的リソースの詳細については、次を参照してください。、 [XAML リソース](xaml-resources.md)します。  
  
- 含まれている<xref:System.Windows.Freezable>サブオブジェクトを固定することはできません。  
  
 これらの条件が場合`false`の<xref:System.Windows.Freezable>オブジェクトする予定がない変更を固定するパフォーマンスを向上することを検討してください。  
  
## <a name="example"></a>例  
 次の例では、フリーズ、<xref:System.Windows.Media.SolidColorBrush>の型である<xref:System.Windows.Freezable>オブジェクト。  
  
 [!code-csharp[freezablesample_procedural#FreezeExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#freezeexample1)]
 [!code-vb[freezablesample_procedural#FreezeExample1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#freezeexample1)]  
  
 詳細については<xref:System.Windows.Freezable>、オブジェクトを参照してください、 [Freezable オブジェクトの概要](freezable-objects-overview.md)します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Freezable>
- <xref:System.Windows.Freezable.CanFreeze%2A>
- <xref:System.Windows.Freezable.Freeze%2A>
- [Freezable オブジェクトの概要](freezable-objects-overview.md)
- [方法トピック](base-elements-how-to-topics.md)
