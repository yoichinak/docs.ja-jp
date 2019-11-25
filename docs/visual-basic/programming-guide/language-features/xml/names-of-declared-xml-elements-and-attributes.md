---
title: 宣言する XML 要素と属性の名前
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [XML in Visual Basic]
- element names [XML in Visual Basic]
- names in XML literals [Visual Basic]
- attribute names [XML in Visual Basic]
- XML literals [Visual Basic], element names
ms.assetid: cc110118-b6cf-4ff9-a4e4-6233c90c9fbf
ms.openlocfilehash: 12fbd1f4332391b1acdcf12e101d82627ebbeaff
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74335996"
---
# <a name="names-of-declared-xml-elements-and-attributes-visual-basic"></a>宣言する XML 要素と属性の名前 (Visual Basic)
This topic provides Visual Basic guidelines for naming XML elements and attributes in XML literals.  In an XML literal, you can specify a local name or a qualified name. A qualified name consists of an XML namespace prefix, a colon, and a local name. For more information about XML namespace prefixes, see [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).  
  
## <a name="rules"></a>ルール  
 A local name of an element or attribute in Visual Basic must adhere to the following rules.  
  
- It can begin with a namespace. It must begin with an alphabetical character or an underscore (`_`).  
  
- It must contain only alphabetical characters, decimal digits, underscores, periods (.), and hyphens (-).  
  
- It must not be more than 1,024 characters long.  
  
- Colons that appear in names indicate namespace demarcation. Therefore, you can use colons only to specify an XML namespace for a particular name.  
  
 In addition, you should adhere to the following guideline.  
  
- The XML 1.0 specification reserves all names starting with the string "xml", of any capitalization variation. Therefore, do not use those names for your element and attribute names.  
  
### <a name="name-length-guidelines"></a>Name Length Guidelines  
 As a practical matter, a name should be as short as possible while still clearly identifying the nature of the element. This improves the readability of your code and reduces line length and source-file size.  
  
 However, your name should not be so short that it does not adequately describe the element or how your code uses it. This is important for the readability of your code. If somebody else is trying to understand it, or if you yourself are looking at it a long time after you wrote it, appropriate element names can save time.  
  
## <a name="case-sensitivity-in-names"></a>Case Sensitivity in Names  
 XML element names are case sensitive. This means that when the Visual Basic compiler compares two names that differ in alphabetical case only, it interprets them as different names. For example, it interprets `ABC` and `abc` as referring to separate elements.  
  
## <a name="xml-namespaces"></a>XML 名前空間  
 When creating an XML element literal, you can specify the XML namespace prefix for the element name. For more information, see [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).  
  
## <a name="see-also"></a>関連項目

- [Visual Basic での XML の作成](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [XML 要素リテラル](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
