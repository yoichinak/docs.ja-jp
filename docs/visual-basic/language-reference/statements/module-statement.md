---
title: Module ステートメント
ms.date: 07/20/2015
f1_keywords:
- Module
- vb.Module
helpviewer_keywords:
- modules, classes
- modules
- Module statement [Visual Basic]
- modules, declaring
- standard modules
- classes [Visual Basic], vs. modules
- declarations [Visual Basic], modules
ms.assetid: a1243afc-14a5-45df-95d5-51118aeac362
ms.openlocfilehash: 56fc4f9383f1fc4779358ef18a4e5c611d897eda
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348013"
---
# <a name="module-statement"></a>Module ステートメント

Declares the name of a module and introduces the definition of the variables, properties, events, and procedures that the module comprises.

## <a name="syntax"></a>構文

```vb
[ <attributelist> ] [ accessmodifier ]  Module name
    [ statements ]
End Module
```

## <a name="parts"></a>指定項目

`attributelist`  
省略可能です。 See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).

`accessmodifier`  
省略可能です。 次のいずれかの値を指定します。

- [Public](../../../visual-basic/language-reference/modifiers/public.md)

- [Friend](../../../visual-basic/language-reference/modifiers/friend.md)

「 [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)」を参照してください。

`name`  
必須です。 Name of this module. 「 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)」を参照してください。

`statements`  
省略可能です。 Statements which define the variables, properties, events, procedures, and nested types of this module.

`End Module`  
`Module` の定義を終了します。

## <a name="remarks"></a>Remarks

A `Module` statement defines a reference type available throughout its namespace. A *module* (sometimes called a *standard module*) is similar to a class but with some important distinctions. Every module has exactly one instance and does not need to be created or assigned to a variable. Modules do not support inheritance or implement interfaces. Notice that a module is not a *type* in the sense that a class or structure is — you cannot declare a programming element to have the data type of a module.

You can use `Module` only at namespace level. This means the *declaration context* for a module must be a source file or namespace, and cannot be a class, structure, module, interface, procedure, or block. You cannot nest a module within another module, or within any type. 詳細については、「[宣言コンテキストと既定のアクセス レベル](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)」を参照してください。

A module has the same lifetime as your program. Because its members are all `Shared`, they also have lifetimes equal to that of the program.

Modules default to [Friend](../../../visual-basic/language-reference/modifiers/friend.md) access. アクセス修飾子を使用してこれらのアクセス レベルを調整できます。 For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).

All members of a module are implicitly `Shared`.

## <a name="classes-and-modules"></a>Classes and Modules

These elements have many similarities, but there are some important differences as well.

- **Terminology.** Previous versions of Visual Basic recognize two types of modules: *class modules* (.cls files) and *standard modules* (.bas files). The current version calls these *classes* and *modules*, respectively.

- **Shared Members.** You can control whether a member of a class is a shared or instance member.

- **Object Orientation.** Classes are object-oriented, but modules are not. So only classes can be instantiated as objects. For more information, see [Objects and Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).

## <a name="rules"></a>ルール

- **Modifiers.** All module members are implicitly [Shared](../../../visual-basic/language-reference/modifiers/shared.md). You cannot use the `Shared` keyword when declaring a member, and you cannot alter the shared status of any member.

- **継承。** A module cannot inherit from any type other than <xref:System.Object>, from which all modules inherit. In particular, one module cannot inherit from another.

  You cannot use the [Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md) in a module definition, even to specify <xref:System.Object>.

- **Default Property.** You cannot define any default properties in a module. For more information, see [Default](../../../visual-basic/language-reference/modifiers/default.md).

## <a name="behavior"></a>動作

- **Access Level.** Within a module, you can declare each member with its own access level. Module members default to [Public](../../../visual-basic/language-reference/modifiers/public.md) access, except variables and constants, which default to [Private](../../../visual-basic/language-reference/modifiers/private.md) access. When a module has more restricted access than one of its members, the specified module access level takes precedence.

- **Scope.** A module is in scope throughout its namespace.

  The scope of every module member is the entire module. Notice that all members undergo *type promotion*, which causes their scope to be promoted to the namespace containing the module. For more information, see [Type Promotion](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).

- **Qualification.** You can have multiple modules in a project, and you can declare members with the same name in two or more modules. However, you must qualify any reference to such a member with the appropriate module name if the reference is from outside that module. 詳細については、「 [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)」を参照してください。

## <a name="example"></a>例

[!code-vb[VbVbalrStatements#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#69)]

## <a name="see-also"></a>関連項目

- [Class ステートメント](../../../visual-basic/language-reference/statements/class-statement.md)
- [Namespace ステートメント](../../../visual-basic/language-reference/statements/namespace-statement.md)
- [Structure ステートメント](../../../visual-basic/language-reference/statements/structure-statement.md)
- [Interface ステートメント](../../../visual-basic/language-reference/statements/interface-statement.md)
- [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)
- [型の上位変換](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md)
