---
title: 型 <typename> は CLS に準拠していません。
ms.date: 07/20/2015
f1_keywords:
- bc40041
- vbc40041
helpviewer_keywords:
- BC40041
ms.assetid: 634132c2-5646-44aa-98c6-f773e2e63882
ms.openlocfilehash: 2805cac71cb36d21f5ab21a5875183803d07a4b4
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65642367"
---
# <a name="type-typename-is-not-cls-compliant"></a>型 \<typename> は CLS に準拠していません
変数、プロパティ、または関数の戻り値が、CLS に準拠していないデータ型で宣言されています。  
  
 アプリケーションを[言語への非依存性および言語非依存コンポーネント](../../../standard/language-independence-and-language-independent-components.md) (CLS) に準拠させるには、CLS 準拠型のみを使用する必要があります。  
  
 次の Visual Basic データ型は CLS に準拠していません。  
  
- [SByte データ型](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
- [UInteger データ型](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
- [ULong データ型](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
- [UShort データ型](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 **エラー ID:** BC40041  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
- アプリケーションを CLS 準拠にする必要がある場合は、この要素のデータ型を、最も近い CLS 準拠型に変更します。 たとえば、2,147,483,647 を超える値の範囲が不要な場合は、 `UInteger` の代わりに `Integer` を使用できます。 拡張範囲が必要な場合は、 `UInteger` の代わりに `Long`を使用できます。  
  
- アプリケーションを CLS 準拠にする必要がない場合は、何も変更する必要はありません。 ただし、準拠していないことを認識している必要があります。
