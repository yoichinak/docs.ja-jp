---
title: '方法: リフレクションを使用せずに印刷システム オブジェクトのプロパティを取得する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PrintSystemObject [WPF], getting properties
ms.assetid: 43560f28-183d-41c1-b9d1-de7c2552273e
ms.openlocfilehash: bb906dafd98e75708764b5f0f009900719f6a475
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59335200"
---
# <a name="how-to-get-print-system-object-properties-without-reflection"></a>方法: リフレクションを使用せずに印刷システム オブジェクトのプロパティを取得する
リフレクションを使用してオブジェクトのプロパティ (およびそれらのプロパティの種類) と、アプリケーションのパフォーマンスが低下することができます。 <xref:System.Printing.IndexedProperties>名前空間でリフレクションを使用して、この情報を取得するための手段を提供します。  
  
## <a name="example"></a>例  
 これを行うための手順は次のとおりです。  
  
1. 型のインスタンスを作成します。 次の例では、型は、<xref:System.Printing.PrintQueue>とほぼ同じコードではなく Microsoft .NET Framework に付属する型から派生した型に対しては機能する必要があります<xref:System.Printing.PrintSystemObject>します。  
  
2. 作成、<xref:System.Printing.IndexedProperties.PrintPropertyDictionary>型から<xref:System.Printing.PrintSystemObject.PropertiesCollection%2A>します。 <xref:System.Collections.DictionaryEntry.Value%2A>このディクショナリ内の各エントリのプロパティから派生した型の 1 つのオブジェクトである<xref:System.Printing.IndexedProperties.PrintProperty>します。  
  
3. ディクショナリのメンバーを列挙します。 それらのそれぞれについて、次の操作を行います。  
  
4. アップ キャストするには、各エントリの値<xref:System.Printing.IndexedProperties.PrintProperty>使用して作成して、<xref:System.Printing.IndexedProperties.PrintProperty>オブジェクト。  
  
5. 型を取得、<xref:System.Printing.IndexedProperties.PrintProperty.Value%2A>のそれぞれの<xref:System.Printing.IndexedProperties.PrintProperty>オブジェクト。  
  
 [!code-csharp[GetPrintObjectPropertyTypesWithoutReflection#ShowPropertyTypesWithoutReflection](~/samples/snippets/csharp/VS_Snippets_Wpf/GetPrintObjectPropertyTypesWithoutReflection/CSharp/Program.cs#showpropertytypeswithoutreflection)]
 [!code-vb[GetPrintObjectPropertyTypesWithoutReflection#ShowPropertyTypesWithoutReflection](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GetPrintObjectPropertyTypesWithoutReflection/visualbasic/program.vb#showpropertytypeswithoutreflection)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Printing.IndexedProperties.PrintProperty>
- <xref:System.Printing.PrintSystemObject>
- <xref:System.Printing.IndexedProperties>
- <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>
- <xref:System.Printing.LocalPrintServer>
- <xref:System.Printing.PrintQueue>
- <xref:System.Collections.DictionaryEntry>
- [WPF のドキュメント](documents-in-wpf.md)
- [印刷の概要](printing-overview.md)
