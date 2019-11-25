---
title: Namespace ステートメント
ms.date: 07/20/2015
f1_keywords:
- vb.Namespace
helpviewer_keywords:
- namespaces [Visual Basic], root
- Namespace statement [Visual Basic]
- namespaces [Visual Basic], nested
- declaring namespaces [Visual Basic], syntax
- namespaces [Visual Basic], declaring
- root namespaces
- declarations [Visual Basic], namespaces
ms.assetid: a31fbd95-9ace-4c3d-bbb1-51222a2272b2
ms.openlocfilehash: 19207a42890640bd82ec547e53eb6d833668e4b5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74329644"
---
# <a name="namespace-statement"></a>Namespace ステートメント
Declares the name of a namespace and causes the source code that follows the declaration to be compiled within that namespace.  
  
## <a name="syntax"></a>構文  
  
```vb  
Namespace [Global.] { name | name.name }  
    [ componenttypes ]  
End Namespace  
```  
  
## <a name="parts"></a>指定項目  
 Global  
 省略可能です。 Allows you to define a namespace out of the root namespace of your project. See [Namespaces in Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md).  
  
 `name`  
 必須です。 A unique name that identifies the namespace. Must be a valid Visual Basic identifier. For more information, see [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
 `componenttypes`  
 省略可能です。 Elements that make up the namespace. These include, but are not limited to, enumerations, structures, interfaces, classes, modules, delegates, and other namespaces.  
  
 `End Namespace`  
 Terminates a `Namespace` block.  
  
## <a name="remarks"></a>Remarks  
 Namespaces are used as an organizational system. They provide a way to classify and present programming elements that are exposed to other programs and applications. Note that a namespace is not a *type* in the sense that a class or structure is—you cannot declare a programming element to have the data type of a namespace.  
  
 All programming elements declared after a `Namespace` statement belong to that namespace. Visual Basic continues to compile elements into the last declared namespace until it encounters either an `End Namespace` statement or another `Namespace` statement.  
  
 If a namespace is already defined, even outside your project, you can add programming elements to it. To do this, you use a `Namespace` statement to direct Visual Basic to compile elements into that namespace.  
  
 You can use a `Namespace` statement only at the file or namespace level. This means the *declaration context* for a namespace must be a source file or another namespace, and cannot be a class, structure, module, interface, or procedure. 詳細については、「[宣言コンテキストと既定のアクセス レベル](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)」を参照してください。  
  
 You can declare one namespace within another. There is no strict limit to the levels of nesting you can declare, but remember that when other code accesses the elements declared in the innermost namespace, it must use a qualification string that contains all the namespace names in the nesting hierarchy.  
  
## <a name="access-level"></a>Access Level  
 Namespaces are treated as if they have a `Public` access level. A namespace can be accessed from code anywhere in the same project, from other projects that reference the project, and from any assembly built from the project.  
  
 Programming elements declared at namespace level, meaning in a namespace but not inside any other element, can have `Public` or `Friend` access. If unspecified, the access level of such an element uses `Friend` by default. Elements you can declare at namespace level include classes, structures, modules, interfaces, enumerations, and delegates. 詳細については、「[宣言コンテキストと既定のアクセス レベル](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)」を参照してください。  
  
## <a name="root-namespace"></a>Root Namespace  
 All namespace names in your project are based on a *root namespace*. Visual Studio では、プロジェクト内のすべてのコードで、既定のルート名前空間としてプロジェクト名が割り当てられます。 たとえば、プロジェクト名が `Payroll`である場合、そのプログラミング要素は `Payroll`名前空間に属します。 If you declare `Namespace funding`, the full name of that namespace is `Payroll.funding`.  
  
 If you want to specify an existing namespace in a `Namespace` statement, such as in the generic list class example, you can set your root namespace to a null value. To do this, click **Project Properties** from the **Project** menu and then clear the **Root namespace** entry so that the box is empty. If you did not do this in the generic list class example, the Visual Basic compiler would take `System.Collections.Generic` as a new namespace within project `Payroll`, with the full name of `Payroll.System.Collections.Generic`.  
  
 Alternatively, you can use the `Global` keyword to refer to elements of namespaces defined outside your project. Doing so lets you retain your project name as the root namespace. This reduces the chance of unintentionally merging your programming elements together with those of existing namespaces. For more information, see the "Global Keyword in Fully Qualified Names" section in [Namespaces in Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md).  
  
 The `Global` keyword can also be used in a Namespace statement. これにより、プロジェクトのルート名前空間から名前空間を定義できます。 For more information, see the "Global Keyword in Namespace Statements" section in [Namespaces in Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md).  
  
 **Troubleshooting.** The root namespace can lead to unexpected concatenations of namespace names. If you make reference to namespaces defined outside your project, the Visual Basic compiler can construe them as nested namespaces in the root namespace. In such a case, the compiler does not recognize any types that have been already defined in the external namespaces. To avoid this, either set your root namespace to a null value as described in "Root Namespace," or use the `Global` keyword to access elements of external namespaces.  
  
## <a name="attributes-and-modifiers"></a>Attributes and Modifiers  
 You cannot apply attributes to a namespace. An attribute contributes information to the assembly's metadata, which is not meaningful for source classifiers such as namespaces.  
  
 You cannot apply any access or procedure modifiers, or any other modifiers, to a namespace. Because it is not a type, these modifiers are not meaningful.  
  
## <a name="example"></a>例  
 The following example declares two namespaces, one nested in the other.  
  
 [!code-vb[VbVbalrStatements#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#43)]  
  
## <a name="example"></a>例  
 The following example declares multiple nested namespaces on a single line, and it is equivalent to the previous example.  
  
 [!code-vb[VbVbalrStatements#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#41)]  
  
## <a name="example"></a>例  
 The following example accesses the class defined in the previous examples.  
  
 [!code-vb[VbVbalrStatements#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#42)]  
  
## <a name="example"></a>例  
 The following example defines the skeleton of a new generic list class and adds it to the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace.  
  
```vb  
Namespace System.Collections.Generic  
    Class specialSortedList(Of T)  
        Inherits List(Of T)  
        ' Insert code to define the special generic list class.  
    End Class  
End Namespace  
```  
  
## <a name="see-also"></a>関連項目

- [Imports ステートメント (.NET 名前空間および型)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [宣言された要素の名前](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [Namespaces in Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)
