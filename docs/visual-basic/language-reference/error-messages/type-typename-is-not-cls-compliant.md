---
title: 型 <typename> は CLS に準拠していません。
ms.date: 07/20/2015
f1_keywords:
- bc40041
- vbc40041
helpviewer_keywords:
- BC40041
ms.assetid: 634132c2-5646-44aa-98c6-f773e2e63882
ms.openlocfilehash: 4adbf38e448dad7634a4336d20b3fce8702be1db
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64664273"
---
# <a name="type-typename-is-not-cls-compliant"></a>型\<typename > CLS 準拠ではありません
変数、プロパティ、または関数の戻り値は、CLS 準拠でないデータ型で宣言されています。  
  
 準拠するアプリケーションの[Language Independence and Language-independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS) に CLS 準拠型のみを使用する必要があります。  
  
 次の Visual Basic データ型は CLS 準拠ではありません。  
  
- [SByte データ型](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
- [UInteger データ型](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
- [ULong データ型](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
- [UShort データ型](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 **エラー ID:** BC40041  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
- アプリケーションは、CLS に準拠する必要がある、最も近い CLS 準拠型にこの要素のデータ型を変更します。 たとえば、2,147,483,647 を超える値の範囲が不要な場合は、 `UInteger` の代わりに `Integer` を使用できます。 拡張範囲が必要な場合は、 `UInteger` の代わりに `Long`を使用できます。  
  
- 場合は、アプリケーションは、CLS に準拠する必要はありません、何も変更する必要はありません。 おく必要がある、コンプライアンス非対応意識ただしします。