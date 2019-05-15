---
title: メンバー '<membername>' の型は CLS に準拠していません。
ms.date: 07/20/2015
f1_keywords:
- bc40025
- vbc40025
helpviewer_keywords:
- BC40025
ms.assetid: adbd34bb-43d2-4266-90e7-cd1afaf49b4e
ms.openlocfilehash: f6f66617774dccff4450cce42904126acf5c3769
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2019
ms.locfileid: "65590689"
---
# <a name="type-of-member-membername-is-not-cls-compliant"></a>メンバーの型 '\<membername >' は CLS 準拠
このメンバーが指定されたデータ型の一部、 [Language Independence and Language-independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS)。 これは、.NET Framework および Visual Basic は、このデータ型をサポートするため、コンポーネント内でエラーではありません。 ただし、厳密に CLS 準拠コードで記述された別のコンポーネントでは、このデータ型がサポートしない可能性があります。 このようなコンポーネントはできないコンポーネントを正常にやり取りすることがあります。  
  
 次の Visual Basic データ型は CLS 準拠ではありません。  
  
- [SByte データ型](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
- [UInteger データ型](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
- [ULong データ型](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
- [UShort データ型](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 既定では、このメッセージは警告です。 警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)」を参照してください。  
  
 **エラー ID:** BC40025  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
- コンポーネントは、のみ、他の .NET Framework コンポーネントとのインターフェイスまたはその他のコンポーネントとやり取りしません、何も変更する必要はありません。  
  
- いない .NET Framework 用に記述されたコンポーネントをやり取りする場合がありますできるリフレクションまたはドキュメントについてからのいずれかを判断するこのデータ型がサポートしているかどうか。 その場合、何も変更する必要はありません。  
  
- このデータ型をサポートしていないコンポーネントとやり取りする場合は、最も近い CLS 準拠型で置き換える必要があります。 たとえば、2,147,483,647 を超える値の範囲が不要な場合は、 `UInteger` の代わりに `Integer` を使用できます。 拡張範囲が必要な場合は、 `UInteger` の代わりに `Long`を使用できます。  
  
- オートメーションまたは COM オブジェクトをやり取りする場合は、一部の種類がある .NET Framework の別のデータ幅よりも注意してください。 たとえば、他の多くの環境では `uint` は 16 ビットです。 このようなコンポーネントに 16 ビットの引数を渡す場合の宣言として`UShort`の代わりに`UInteger`管理対象の Visual Basic コードです。  
  
## <a name="see-also"></a>関連項目

- [リフレクション](../../../framework/reflection-and-codedom/reflection.md)
