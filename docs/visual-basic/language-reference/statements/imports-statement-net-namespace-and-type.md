---
title: Imports Statement - .NET Namespace and Type
ms.date: 07/20/2015
f1_keywords:
- vb.Imports
- imports
helpviewer_keywords:
- declared element names [Visual Basic], qualification
- imports [Visual Basic]
- Imports statement [Visual Basic]
- aliases [Visual Basic], Imports statement
- container elements [Visual Basic]
- namespaces [Visual Basic], importing
- Imports statement [Visual Basic], syntax
- import aliases [Visual Basic]
- aliases [Visual Basic], import
- declared elements [Visual Basic], container elements
ms.assetid: 7062f8aa-d890-4232-9eed-92836e13fb6e
ms.openlocfilehash: 39fa4e74f973bcb575b5751c387c0b879f4e398d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351066"
---
# <a name="imports-statement-net-namespace-and-type"></a>Imports ステートメント (.NET 名前空間および型)

Enables type names to be referenced without namespace qualification.

## <a name="syntax"></a>構文

```vb
Imports [ aliasname = ] namespace
' -or-
Imports [ aliasname = ] namespace.element
```

## <a name="parts"></a>指定項目

|用語|定義|
|---|---|
|`aliasname`|省略可能です。 An *import alias* or name by which code can refer to `namespace` instead of the full qualification string. 「 [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md)」を参照してください。|
|`namespace`|必須です。 The fully qualified name of the namespace being imported. Can be a string of namespaces nested to any level.|
|`element`|省略可能です。 The name of a programming element declared in the namespace. Can be any container element.|

## <a name="remarks"></a>Remarks

The `Imports` statement enables types that are contained in a given namespace to be referenced directly.

You can supply a single namespace name or a string of nested namespaces. Each nested namespace is separated from the next higher level namespace by a period (`.`), as the following example illustrates:

```vb
Imports System.Collections.Generic
```

Each source file can contain any number of `Imports` statements. These must follow any option declarations, such as the `Option Strict` statement, and they must precede any programming element declarations, such as `Module` or `Class` statements.

You can use `Imports` only at file level. This means the declaration context for importation must be a source file, and cannot be a namespace, class, structure, module, interface, procedure, or block.

Note that the `Imports` statement does not make elements from other projects and assemblies available to your project. Importing does not take the place of setting a reference. It only removes the need to qualify names that are already available to your project. For more information, see "Importing Containing Elements" in [References to Declared Elements](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).

> [!NOTE]
> You can define implicit `Imports` statements by using the [References Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic). For more information, see [How to: Add or Remove Imported Namespaces (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).

## <a name="import-aliases"></a>インポート エイリアス

An *import alias* defines the alias for a namespace or type. Import aliases are useful when you need to use items with the same name that are declared in one or more namespaces. For more information and an example, see "Qualifying an Element Name" in [References to Declared Elements](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).

You should not declare a member at module level with the same name as `aliasname`. If you do, the Visual Basic compiler uses `aliasname` only for the declared member and no longer recognizes it as an import alias.

Although the syntax used for declaring an import alias is like that used for importing an XML namespace prefix, the results are different. An import alias can be used as an expression in your code, whereas an XML namespace prefix can be used only in XML literals or XML axis properties as the prefix for a qualified element or attribute name.

### <a name="element-names"></a>要素の名前

If you supply `element`, it must represent a *container element*, that is, a programming element that can contain other elements. Container elements include classes, structures, modules, interfaces, and enumerations.

The scope of the elements made available by an `Imports` statement depends on whether you specify `element`. If you specify only `namespace`, all uniquely named members of that namespace, and members of container elements within that namespace, are available without qualification. If you specify both `namespace` and `element`, only the members of that element are available without qualification.

## <a name="example"></a>例

The following example returns all the folders in the *C:\\* directory by using the <xref:System.IO.DirectoryInfo> class:

The code has no `Imports` statements at the top of the file. Therefore, the <xref:System.IO.DirectoryInfo>, <xref:System.Text.StringBuilder>, and <xref:Microsoft.VisualBasic.ControlChars.CrLf> references are all fully qualified with the namespaces.

[!code-vb[VbVbalrStatements#152](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#152)]

## <a name="example"></a>例

The following example includes `Imports` statements for the referenced namespaces. Therefore, the types do not have to be fully qualified with the namespaces.

[!code-vb[VbVbalrStatements#153](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#153)]

[!code-vb[VbVbalrStatements#154](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#154)]
  
## <a name="example"></a>例

The following example includes `Imports` statements that create aliases for the referenced namespaces. The types are qualified with the aliases.

[!code-vb[VbVbalrStatements#155](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#155)]

[!code-vb[VbVbalrStatements#156](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#156)]

## <a name="example"></a>例

The following example includes `Imports` statements that create aliases for the referenced types. Aliases are used to specify the types.

[!code-vb[VbVbalrStatements#157](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#157)]

[!code-vb[VbVbalrStatements#158](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#158)]
  
## <a name="see-also"></a>関連項目

- [Namespace ステートメント](namespace-statement.md)
- [Namespaces in Visual Basic](../../programming-guide/program-structure/namespaces.md)
- [参照と Imports ステートメント](../../programming-guide/program-structure/references-and-the-imports-statement.md)
- [Imports ステートメント (XML 名前空間)](imports-statement-xml-namespace.md)
- [宣言された要素の参照](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
