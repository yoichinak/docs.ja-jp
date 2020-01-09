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
ms.openlocfilehash: 6b202d618d9d2216c8998181303250081de6781c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2020
ms.locfileid: "75708985"
---
# <a name="using-standard-exception-types"></a>標準例外型の使用
このセクションでは、フレームワークによって提供される標準の例外とその使用法の詳細について説明します。 リストは、完全な手段ではありません。 他のフレームワークの例外の種類の使用方法については、.NET Framework リファレンスドキュメントを参照してください。  
  
## <a name="exception-and-systemexception"></a>Exception および SystemException  
 **X DO NOT** スロー<xref:System.Exception?displayProperty=nameWithType>または<xref:System.SystemException?displayProperty=nameWithType>です。  
  
 **X DO NOT** キャッチ`System.Exception`または`System.SystemException`framework コードで再スローする場合を除き、します。  
  
 **X AVOID** キャッチ`System.Exception`または`System.SystemException`、トップレベルの例外ハンドラーでは可します。  
  
## <a name="applicationexception"></a>ApplicationException  
 **X DO NOT** スロー サービスまたはそれから派生<xref:System.ApplicationException>です。  
  
## <a name="invalidoperationexception"></a>InvalidOperationException  
 **✓ DO** スロー、<xref:System.InvalidOperationException>オブジェクトが不適切な状態である場合。  
  
## <a name="argumentexception-argumentnullexception-and-argumentoutofrangeexception"></a>ArgumentException、System.argumentnullexception、ArgumentOutOfRangeException  
 **✓ DO** スロー<xref:System.ArgumentException>またはメンバーに無効な引数が渡された場合は、そのサブタイプのいずれか。 最も派生した例外の種類を優先します (該当する場合)。  
  
 **✓ DO** 設定、`ParamName`プロパティのサブクラスのいずれかをスローするときに`ArgumentException`です。  
  
 このプロパティは、例外がスローされる原因となったパラメーターの名前を表します。 プロパティは、コンストラクターのオーバーロードのいずれかを使用して設定できます。  
  
 **✓ DO** 使用`value`プロパティ set アクセス操作子の暗黙的な値パラメーターの名前。  
  
## <a name="nullreferenceexception-indexoutofrangeexception-and-accessviolationexception"></a>NullReferenceException、IndexOutOfRangeException、および Access Ationexception  
 **X DO NOT** 明示的または暗黙的にスローする、api で公開されている呼び出し可能<xref:System.NullReferenceException>、 <xref:System.AccessViolationException>、または<xref:System.IndexOutOfRangeException>です。 これらの例外は、実行エンジンによって予約およびスローされ、ほとんどの場合、バグを示します。  
  
 これらの例外をスローしないように引数をチェックします。 これらの例外をスローすると、時間の経過と共に変化する可能性のあるメソッドの実装の詳細が表示されます。  
  
## <a name="stackoverflowexception"></a>StackOverflowException  
 **X DO NOT** を明示的にスロー<xref:System.StackOverflowException>です。 例外は、CLR によってのみ明示的にスローされる必要があります。  
  
 **X DO NOT** キャッチ`StackOverflowException`です。  
  
 任意のスタックオーバーフローの有無に一貫性を持たせるマネージコードを記述することはほとんど不可能です。 CLR のアンマネージ部分は、プローブを使用してスタックオーバーフローを適切に定義された場所に移動することによって一貫性を保ちます。これは、任意のスタックオーバーフローからのバックアップではありません。  
  
## <a name="outofmemoryexception"></a>OutOfMemoryException  
 **X DO NOT** を明示的にスロー<xref:System.OutOfMemoryException>です。 この例外は、CLR インフラストラクチャによってのみスローされます。  
  
## <a name="comexception-sehexception-and-executionengineexception"></a>ComException、SEHException、および System.executionengineexception  
 **X DO NOT** を明示的にスロー <xref:System.Runtime.InteropServices.COMException>、 <xref:System.ExecutionEngineException>、および<xref:System.Runtime.InteropServices.SEHException>です。 これらの例外は、CLR インフラストラクチャによってのみスローされます。  
  
 *©2005、2009 Microsoft Corporation の部分。すべての権限が予約されています。*  
  
 *2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*  
  
## <a name="see-also"></a>関連項目

- [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)
- [例外のデザインのガイドライン](../../../docs/standard/design-guidelines/exceptions.md)
