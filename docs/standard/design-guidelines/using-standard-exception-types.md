---
title: 標準例外型の使用
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- throwing exceptions, standard types
- catching exceptions
- exceptions, catching
- exceptions, throwing
ms.assetid: ab22ce03-78f9-4dca-8824-c7ed3bdccc27
author: KrzysztofCwalina
ms.openlocfilehash: b947c7cce057c060b1ab5054d1227f5703ccbf89
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62026338"
---
# <a name="using-standard-exception-types"></a>標準例外型の使用
このセクションでは、フレームワークと、その使用状況の詳細によって提供される標準の例外について説明します。 一覧は完全ではではありません。 その他のフレームワーク例外の種類の使用状況の .NET Framework のリファレンス ドキュメントを参照してください。  
  
## <a name="exception-and-systemexception"></a>例外と SystemException  
 **X DO NOT** スロー<xref:System.Exception?displayProperty=nameWithType>または<xref:System.SystemException?displayProperty=nameWithType>です。  
  
 **X DO NOT** キャッチ`System.Exception`または`System.SystemException`framework コードで再スローする場合を除き、します。  
  
 **X AVOID** キャッチ`System.Exception`または`System.SystemException`、トップレベルの例外ハンドラーでは可します。  
  
## <a name="applicationexception"></a>ApplicationException  
 **X DO NOT** スロー サービスまたはそれから派生<xref:System.ApplicationException>です。  
  
## <a name="invalidoperationexception"></a>InvalidOperationException  
 **✓ DO** スロー、<xref:System.InvalidOperationException>オブジェクトが不適切な状態である場合。  
  
## <a name="argumentexception-argumentnullexception-and-argumentoutofrangeexception"></a>ArgumentException、ArgumentNullException、および argumentoutofrangeexception が発生しました  
 **✓ DO** スロー<xref:System.ArgumentException>またはメンバーに無効な引数が渡された場合は、そのサブタイプのいずれか。 該当する場合は、大多数の派生の例外型を好みます。  
  
 **✓ DO** 設定、`ParamName`プロパティのサブクラスのいずれかをスローするときに`ArgumentException`です。  
  
 このプロパティは、例外がスローされる原因となったパラメーターの名前を表します。 コンス トラクター オーバー ロードのいずれかを使用して、プロパティを設定できることに注意してください。  
  
 **✓ DO** 使用`value`プロパティ set アクセス操作子の暗黙的な値パラメーターの名前。  
  
## <a name="nullreferenceexception-indexoutofrangeexception-and-accessviolationexception"></a>NullReferenceException、IndexOutOfRangeException、および AccessViolationException  
 **X DO NOT** 明示的または暗黙的にスローする、api で公開されている呼び出し可能<xref:System.NullReferenceException>、 <xref:System.AccessViolationException>、または<xref:System.IndexOutOfRangeException>です。 これらの例外に予約されていますとでほとんどの場合は、バグを示す場合、実行エンジンによってスローされます。  
  
 引数をこれらの例外をスローすることを避けるためにチェックを実行します。 これらの例外をスローすることは、時間の経過と共に変わる可能性があるメソッドの実装の詳細を公開します。  
  
## <a name="stackoverflowexception"></a>StackOverflowException  
 **X DO NOT** を明示的にスロー<xref:System.StackOverflowException>です。 CLR によってのみ、例外を明示的にスローされる必要があります。  
  
 **X DO NOT** キャッチ`StackOverflowException`です。  
  
 ほとんどでは、一貫性のある任意のスタック オーバーフローが存在する場合に残っているマネージ コードを記述することはできません。 任意のスタック オーバーフローからバックアップではなく、スタックがオーバーフローして明確に定義された場所に移動するプローブを使用して、整合性、CLR のアンマネージ部分を維持します。  
  
## <a name="outofmemoryexception"></a>OutOfMemoryException  
 **X DO NOT** を明示的にスロー<xref:System.OutOfMemoryException>です。 この例外では、CLR のインフラストラクチャによってのみスローされます。  
  
## <a name="comexception-sehexception-and-executionengineexception"></a>ComException、SEHException、および ExecutionEngineException  
 **X DO NOT** を明示的にスロー <xref:System.Runtime.InteropServices.COMException>、 <xref:System.ExecutionEngineException>、および<xref:System.Runtime.InteropServices.SEHException>です。 これらの例外では、CLR のインフラストラクチャによってのみスローされます。  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 *Pearson Education, Inc. からのアクセス許可によって了承を得て転載[Framework デザイン ガイドライン。規則、手法、および再利用可能な .NET ライブラリの第 2 版のパターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina、Brad 内容では、Microsoft Windows の開発シリーズの一部として、Addison-wesley Professional、2008 年 10 月 22日を公開します。*  
  
## <a name="see-also"></a>関連項目

- [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)
- [例外のデザインのガイドライン](../../../docs/standard/design-guidelines/exceptions.md)
