---
title: '方法: Windows API (Visual Basic) を呼び出す'
ms.date: 07/20/2015
helpviewer_keywords:
- API calls [Visual Basic]
- Windows API, calling
- API calls [Visual Basic], platform invoke
- calls [Visual Basic], stored procedures
ms.assetid: 27d75f0a-54ab-4ee1-b91d-43513a19b12d
ms.openlocfilehash: 3769da28e1c9a27c8363b0d6ec639cedaf0f03be
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64624855"
---
# <a name="how-to-call-windows-apis-visual-basic"></a>方法: Windows API (Visual Basic) を呼び出す
この例はuser32.dll内の `MessageBox` 関数の定義と呼び出しを行い、そして文字列を渡しています。

## <a name="example"></a>例
 [!code-vb[VbVbalrInterop#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#1)]

## <a name="compiling-the-code"></a>コードのコンパイル
 この例で必要な要素は次のとおりです。

- <xref:System> 名前空間への参照

## <a name="robust-programming"></a>信頼性の高いプログラミング
 次の条件を満たす場合は、例外が発生する可能性があります。

- メソッドが静的でない、または抽象メソッドである、または以前に定義されているメソッドの場合。 親の型がインターフェイスである、または*name*や*dllName*の長さが 0 の場合。 (<xref:System.ArgumentException>)

- *name*または*dllName*が`Nothing`の場合。 (<xref:System.ArgumentNullException>)

- 含んでいる型が `CreateType` を使用して以前に作成されている場合。 (<xref:System.InvalidOperationException>)

## <a name="see-also"></a>関連項目

- [プラットフォーム呼び出しの詳細](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)
- [プラットフォーム呼び出しの例](../../../framework/interop/platform-invoke-examples.md)
- [アンマネージ DLL 関数の処理](../../../framework/interop/consuming-unmanaged-dll-functions.md)
- [出力のリフレクションを使用してメソッドを定義します。](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w63y4d4f(v=vs.100))
- [チュートリアル: Windows API の呼び出し](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
- [COM 相互運用](../../../visual-basic/programming-guide/com-interop/index.md)
