---
title: CLS に準拠していない <membername> は、CLS に準拠しているインターフェイスに使用できません。
ms.date: 07/20/2015
f1_keywords:
- bc40033
- vbc40033
helpviewer_keywords:
- BC40033
ms.assetid: 060c4b08-798e-40f1-94cf-c05c524f1b8a
ms.openlocfilehash: 68e1fb4f55d9f9b140f1b54cfde2bc5f60952dd2
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64592137"
---
# <a name="non-cls-compliant-membername-is-not-allowed-in-a-cls-compliant-interface"></a>CLS 準拠インターフェイスでは、CLS に準拠していない \<membername> は許可されません
インターフェイス自体が `<CLSCompliant(False)>` としてマークされているか、またはマークされていない場合、インターフェイス内のプロパティ、プロシージャ、またはイベントは `<CLSCompliant(True)>` としてマークされます。  
  
 インターフェイスを[言語への非依存性および言語非依存コンポーネント](../../../standard/language-independence-and-language-independent-components.md) (CLS) に準拠させるには、そのすべてのメンバーが準拠している必要があります。  
  
 プログラミング要素に <xref:System.CLSCompliantAttribute> を適用する場合は、属性の `isCompliant` パラメーターを `True` または `False` のどちらかに設定して、準拠または非準拠を示します。 このパラメーターには既定値がありません。値を指定する必要があります。  
  
 要素に <xref:System.CLSCompliantAttribute> を適用しないと、その要素は非準拠と見なされます。  
  
 既定では、このメッセージは警告です。 警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)」をご覧ください。  
  
 **エラー ID:** BC40033  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
- CLS への準拠が必要なときに、インターフェイスのソース コードを制御できる場合、そのすべてのメンバーが準拠している場合はインターフェイスを `<CLSCompliant(True)>` としてマークします。  
  
- CLS への準拠が必要なときに、インターフェイスのソース コードを制御できない場合や、インターフェイスのソース コードが準拠のための要件を満たしていない場合は、このメンバーを別のクラス内で定義します。  
  
- このメンバーを現在のインターフェイス内に残すことが必要な場合は、<xref:System.CLSCompliantAttribute> をその定義から削除するか、または `<CLSCompliant(False)>` としてマークします。  
  
## <a name="see-also"></a>関連項目

- [Interface ステートメント](../../../visual-basic/language-reference/statements/interface-statement.md)
