---
title: enum の基になる型 '<typename>' は CLS に準拠していません。
ms.date: 07/20/2015
f1_keywords:
- vbc40032
- bc40032
helpviewer_keywords:
- BC40032
ms.assetid: 32bf1949-fd73-456c-a323-bf1ffe1320ed
ms.openlocfilehash: 7d4566637da74726867c55ddf89b965d055e5d14
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2019
ms.locfileid: "65589922"
---
# <a name="underlying-type-typename-of-enum-is-not-cls-compliant"></a>enum の基になる型 \<typename> は CLS に準拠していません
この列挙型に指定されたデータ型は、[言語への非依存性、および言語非依存コンポーネント](../../../standard/language-independence-and-language-independent-components.md) (CLS) の一部ではありません。 .NET Framework と Visual Basic では、このデータ型をサポートしているため、コンポーネント内でエラーにはなりません。 ただし、厳密に CLS に準拠しているコードで記述された別のコンポーネントでは、このデータ型をサポートしていない可能性があります。 そのようなコンポーネントでは、使用しているコンポーネントと正常にやり取りできない場合があります。  
  
 次の Visual Basic データ型は CLS に準拠していません。  
  
- [SByte データ型](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
- [UInteger データ型](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
- [ULong データ型](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
- [UShort データ型](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 既定では、このメッセージは警告です。 警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)」を参照してください。  
  
 **エラー ID:** BC40032  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
- コンポーネントが他の .NET Framework コンポーネントとのみやり取りする場合、または他のコンポーネントとやり取りしない場合は、何も変更する必要はありません。  
  
- .NET Framework 用に記述されていないコンポーネントとやり取りする場合は、リフレクションを通じて、またはドキュメントからこのデータ型がサポートされているかどうかを判断できます。 サポートされている場合は、何も変更する必要はありません。  
  
- このデータ型をサポートしていないコンポーネントとやり取りする場合は、それを最も近い CLS 準拠の型に置き換える必要があります。 たとえば、2,147,483,647 を超える値の範囲が不要な場合は、 `UInteger` の代わりに `Integer` を使用できます。 拡張範囲が必要な場合は、 `UInteger` の代わりに `Long`を使用できます。  
  
- オートメーション オブジェクトや COM オブジェクトとやり取りする場合は、一部の型のデータ幅が .NET Framework とは異なることに注意してください。 たとえば、他の多くの環境では `uint` は 16 ビットです。 そのようなコンポーネントに 16 ビットの引数を渡す場合は、Visual Basic のマネージド コードで、`UInteger` ではなく `UShort` として宣言します。  
  
## <a name="see-also"></a>関連項目

- [リフレクション (Visual Basic)](../../programming-guide/concepts/reflection.md)
- [リフレクション](../../../framework/reflection-and-codedom/reflection.md)
