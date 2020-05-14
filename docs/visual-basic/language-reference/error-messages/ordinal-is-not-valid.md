---
title: 序数が有効ではありません。
ms.date: 07/20/2015
f1_keywords:
- vbrID452
ms.assetid: 7459562b-cd4f-4590-95e0-6126ae3589a5
ms.openlocfilehash: 740243c744a7ba5391659894812a00d80555fd80
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665662"
---
# <a name="ordinal-is-not-valid"></a>序数が有効ではありません。
ダイナミック リンク ライブラリ (DLL) への呼び出しが、`#num` 構文を使用して、プロシージャ名の代わりに数値を使用するように指定されています。 このエラーには、次のような原因が考えられます。  
  
- `#num` 式を序数に変換しようとして失敗しました。  
  
- 指定された `#num` が、DLL 内の関数を指定していません。  
  
- タイプ ライブラリに無効な宣言が含まれているため、無効な序数が内部で使用されています。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1. 式が有効な数値を表していること、または名前によってプロシージャを呼び出していることを確認します。  
  
2. `#num` が DLL 内の有効な関数を識別することを確認します。  
  
3. コードをコメント アウトすることで、問題の原因となっているプロシージャ呼び出しを分離します。 プロシージャの `Declare` ステートメントを記述し、その問題をタイプ ライブラリのベンダーに報告します。  
  
## <a name="see-also"></a>関連項目

- [Declare ステートメント](../../../visual-basic/language-reference/statements/declare-statement.md)
