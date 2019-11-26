---
title: Interface ステートメント
ms.date: 05/12/2018
f1_keywords:
- vb.Interface
helpviewer_keywords:
- interface statement [Visual Basic]
- interfaces [Visual Basic], interface definition
ms.assetid: 8997af73-bda3-4f79-bd41-ca396b610260
ms.openlocfilehash: b606f24cf3baa13746834dfbf7ca6b9215fd3558
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348056"
---
# <a name="interface-statement-visual-basic"></a>Interface ステートメント (Visual Basic)
Declares the name of an interface and introduces the definitions of the members that the interface comprises.  
  
## <a name="syntax"></a>構文  
  
```vb  
[ <attributelist> ] [ accessmodifier ] [ Shadows ] _  
Interface name [ ( Of typelist ) ]  
    [ Inherits interfacenames ]  
    [ [ modifiers ] Property membername ]  
    [ [ modifiers ] Function membername ]  
    [ [ modifiers ] Sub membername ]  
    [ [ modifiers ] Event membername ]  
    [ [ modifiers ] Interface membername ]  
    [ [ modifiers ] Class membername ]  
    [ [ modifiers ] Structure membername ]  
End Interface  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`attributelist`|省略可能です。 See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).|  
|`accessmodifier`|省略可能です。 次のいずれかの値を指定します。<br /><br /> -   [Public](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [Private](../../../visual-basic/language-reference/modifiers/private.md)<br />-  [Protected Friend](../../language-reference/modifiers/protected-friend.md)<br/>- [Private Protected](../../language-reference/modifiers/private-protected.md)<br /><br /> 「 [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)」を参照してください。|  
|`Shadows`|省略可能です。 See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).|  
|`name`|必須です。 Name of this interface. 「 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)」を参照してください。|  
|`Of`|省略可能です。 Specifies that this is a generic interface.|  
|`typelist`|Required if you use the [Of](../../../visual-basic/language-reference/statements/of-clause.md) keyword. List of type parameters for this interface. Optionally, each type parameter can be declared variant by using `In` and `Out` generic modifiers. See [Type List](../../../visual-basic/language-reference/statements/type-list.md).|  
|`Inherits`|省略可能です。 Indicates that this interface inherits the attributes and members of another interface or interfaces. See [Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md).|  
|`interfacenames`|`Inherits` ステートメントを使用する場合は必ず指定します。 The names of the interfaces from which this interface derives.|  
|`modifiers`|省略可能です。 Appropriate modifiers for the interface member being defined.|  
|`Property`|省略可能です。 Defines a property that is a member of the interface.|  
|`Function`|省略可能です。 Defines a `Function` procedure that is a member of the interface.|  
|`Sub`|省略可能です。 Defines a `Sub` procedure that is a member of the interface.|  
|`Event`|省略可能です。 Defines an event that is a member of the interface.|  
|`Interface`|省略可能です。 Defines an interface that is a nested within this interface. The nested interface definition must terminate with an `End Interface` statement.|  
|`Class`|省略可能です。 Defines a class that is a member of the interface. The member class definition must terminate with an `End Class` statement.|  
|`Structure`|省略可能です。 Defines a structure that is a member of the interface. The member structure definition must terminate with an `End Structure` statement.|  
|`membername`|Required for each property, procedure, event, interface, class, or structure defined as a member of the interface. メンバーの名前。|  
|`End Interface`|`Interface` の定義を終了します。|  
  
## <a name="remarks"></a>Remarks  
 An *interface* defines a set of members, such as properties and procedures, that classes and structures can implement. The interface defines only the signatures of the members and not their internal workings.  
  
 A class or structure implements the interface by supplying code for every member defined by the interface. Finally, when the application creates an instance from that class or structure, an object exists and runs in memory. For more information, see [Objects and Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md) and [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md).  
  
 `Interface` は、名前空間またはモジュール レベルでのみ使用できます。 This means the *declaration context* for an interface must be a source file, namespace, class, structure, module, or interface, and cannot be a procedure or block. 詳細については、「[宣言コンテキストと既定のアクセス レベル](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)」を参照してください。  
  
 Interfaces default to [Friend](../../../visual-basic/language-reference/modifiers/friend.md) access. アクセス修飾子を使用してこれらのアクセス レベルを調整できます。 For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="rules"></a>ルール  
  
- **Nesting Interfaces.** You can define one interface within another. The outer interface is called the *containing interface*, and the inner interface is called a *nested interface*.  
  
- **Member Declaration.** When you declare a property or procedure as a member of an interface, you are defining only the *signature* of that property or procedure. This includes the element type (property or procedure), its parameters and parameter types, and its return type. Because of this, the member definition uses only one line of code, and terminating statements such as `End Function` or `End Property` are not valid in an interface.  
  
     In contrast, when you define an enumeration or structure, or a nested class or interface, it is necessary to include their data members.  
  
- **Member Modifiers.** You cannot use any access modifiers when defining module members, nor can you specify [Shared](../../../visual-basic/language-reference/modifiers/shared.md) or any procedure modifier except [Overloads](../../../visual-basic/language-reference/modifiers/overloads.md). You can declare any member with [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md), and you can use [Default](../../../visual-basic/language-reference/modifiers/default.md) when defining a property, as well as [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md) or [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md).  
  
- **継承。** If the interface uses the [Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md), you can specify one or more base interfaces. You can inherit from two interfaces even if they each define a member with the same name. If you do so, the implementing code must use name qualification to specify which member it is implementing.  
  
     An interface cannot inherit from another interface with a more restrictive access level. For example, a `Public` interface cannot inherit from a `Friend` interface.  
  
     An interface cannot inherit from an interface nested within it.  
  
- **Implementation.** When a class uses the [Implements](../../../visual-basic/language-reference/statements/implements-clause.md) statement to implement this interface, it must implement every member defined within the interface. Furthermore, each signature in the implementing code must exactly match the corresponding signature defined in this interface. However, the name of the member in the implementing code does not have to match the member name as defined in the interface.  
  
     When a class is implementing a procedure, it cannot designate the procedure as `Shared`.  
  
- **Default Property.** An interface can specify at most one property as its *default property*, which can be referenced without using the property name. You specify such a property by declaring it with the [Default](../../../visual-basic/language-reference/modifiers/default.md) modifier.  
  
     Notice that this means that an interface can define a default property only if it inherits none.  
  
## <a name="behavior"></a>動作  
  
- **Access Level.** All interface members implicitly have [Public](../../../visual-basic/language-reference/modifiers/public.md) access. You cannot use any access modifier when defining a member. However, a class implementing the interface can declare an access level for each implemented member.  
  
     If you assign a class instance to a variable, the access level of its members can depend on whether the data type of the variable is the underlying interface or the implementing class. 次に例を示します。  
  
     [!code-vb[VbVbalrStatements#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#39)]  
  
     If you access class members through `varAsInterface`, they all have public access. However, if you access members through `varAsClass`, the `Sub` procedure `doSomething` has private access.  
  
- **Scope.** An interface is in scope throughout its namespace, class, structure, or module.  
  
     The scope of every interface member is the entire interface.  
  
- **Lifetime.** An interface does not itself have a lifetime, nor do its members. When a class implements an interface and an object is created as an instance of that class, the object has a lifetime within the application in which it is running. For more information, see "Lifetime" in [Class Statement](../../../visual-basic/language-reference/statements/class-statement.md).  
  
## <a name="example"></a>例  
 The following example uses the `Interface` statement to define an interface named `thisInterface`, which must be implemented with a `Property` statement and a `Function` statement.  
  
 [!code-vb[VbVbalrStatements#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#40)]  
  
 Note that the `Property` and `Function` statements do not introduce blocks ending with `End Property` and `End Function` within the interface. The interface defines only the signatures of its members. The full `Property` and `Function` blocks appear in a class that implements `thisInterface`.  
  
## <a name="see-also"></a>関連項目

- [インターフェイス](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
- [Class ステートメント](../../../visual-basic/language-reference/statements/class-statement.md)
- [Module ステートメント](../../../visual-basic/language-reference/statements/module-statement.md)
- [Structure ステートメント](../../../visual-basic/language-reference/statements/structure-statement.md)
- [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)
- [Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)
- [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [ジェネリック インターフェイスの変性](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)
- [Out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
