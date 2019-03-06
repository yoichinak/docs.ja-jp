---
title: '方法: Freezable が固定されているかどうかを判別する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Freezable objects [WPF], determining if frozen
ms.assetid: 92e58baa-ee12-4a9e-ac3a-ca458807a8b2
ms.openlocfilehash: 005bb27803830a2e38a7b143d2c4cff669ad1da6
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57362514"
---
# <a name="how-to-determine-whether-a-freezable-is-frozen"></a>方法: Freezable が固定されているかどうかを判別する
この例を確認する方法を示して かどうかを<xref:System.Windows.Freezable>オブジェクトが固定されています。 固定された変更を行う場合<xref:System.Windows.Freezable>オブジェクトがスローされます、<xref:System.InvalidOperationException>します。 この例外をスローすることを避けるため、使用、<xref:System.Windows.Freezable.IsFrozen%2A>のプロパティ、<xref:System.Windows.Freezable>が固定されているかどうかを判断するオブジェクト。  
  
## <a name="example"></a>例  
 次の例では、フリーズ、<xref:System.Windows.Media.SolidColorBrush>を使用してテストし、その、<xref:System.Windows.Freezable.IsFrozen%2A>が固定されているかどうかを決定するプロパティ。  
  
 [!code-csharp[freezablesample_procedural#CheckIsFrozenExample](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#checkisfrozenexample)]
 [!code-vb[freezablesample_procedural#CheckIsFrozenExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#checkisfrozenexample)]  
  
 詳細については<xref:System.Windows.Freezable>、オブジェクトを参照してください、 [Freezable オブジェクトの概要](freezable-objects-overview.md)します。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Freezable>
- <xref:System.Windows.Freezable.IsFrozen%2A>
- [Freezable オブジェクトの概要](freezable-objects-overview.md)
- [方法トピック](base-elements-how-to-topics.md)
