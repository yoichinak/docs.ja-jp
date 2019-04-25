---
title: XML リテラルおよび XML プロパティは、ASP.NET 内の埋め込みコードではサポートされません
ms.date: 07/20/2015
f1_keywords:
- vbc31200
- bc31200
helpviewer_keywords:
- BC31200
ms.assetid: 053e8cba-8584-45cc-9fa0-43d122779772
ms.openlocfilehash: 79be695478983055ae1f016cf841d733d3f4c430
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58813926"
---
# <a name="xml-literals-and-xml-properties-are-not-supported-in-embedded-code-within-aspnet"></a>XML リテラルおよび XML プロパティは、ASP.NET 内の埋め込みコードではサポートされません
ASP.NET 内の埋め込みコードでは、XML リテラルおよび XML プロパティがサポートされていません。 XML の機能を使用するには、分離コードにコードを移動します。  
  
 埋め込みコード内で、XML リテラルまたは XML 軸プロパティが定義されている (`<%= =>`) で、ASP.NET ファイル。  
  
 **エラー ID:** BC31200  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   ASP.NET 分離コード ファイルにコードを含む XML リテラルまたは XML 軸プロパティを移動します。  
  
## <a name="see-also"></a>関連項目

- [XML リテラル](../../../visual-basic/language-reference/xml-literals/index.md)
- [XML 軸プロパティ](../../../visual-basic/language-reference/xml-axis/index.md)
- [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)
