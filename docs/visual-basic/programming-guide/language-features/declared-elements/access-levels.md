---
title: Visual Basic でのアクセス レベル
ms.date: 05/10/2018
helpviewer_keywords:
- members [Visual Basic], accessing in Visual Basic
- Friend access modifier
- access levels, declared elements
- access levels
- access modifiers
- Public access modifier
- Protected access modifier
- Protected Friend access modifier
- Private Protected access modifier
- Private access modifier
- declared elements [Visual Basic], access level
ms.assetid: 6e06c1ab-fd78-47f0-83a8-1152780b5e1a
ms.openlocfilehash: d8f2f16d2fb15f2e840f13f177d3fea83fda315e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58843103"
---
# <a name="access-levels-in-visual-basic"></a>Visual Basic でのアクセス レベル
*アクセス レベル*程度にアクセスできるは、宣言された要素のどのようなコードは、読み取りし、書き込みをするアクセス許可。 これは、アクセス レベルは、要素自体を宣言する方法だけでなく、要素のコンテナーのアクセス レベルによっても決定されます。 として宣言も含めに含まれる要素のいずれかが含まれている要素にアクセスできないコードにアクセスできない、`Public`します。 など、`Public`で変数を`Private`構造体からは、構造体を含むクラスの内部からアクセスできるそのクラスの外部。  
  
## <a name="public"></a>Public  
 [パブリック](../../../../visual-basic/language-reference/modifiers/public.md)宣言ステートメントのキーワードは、同じプロジェクト内、プロジェクトを参照する他のプロジェクトおよびプロジェクトからビルドされたアセンブリから、要素にアクセスできることを指定します。 次のコードはサンプル`Public`宣言します。  
  
```vb  
Public Class classForEverybody  
```  
  
 使用することができます`Public`モジュール、インターフェイス、または名前空間レベルでのみです。 つまり、レベル内で、インターフェイス、モジュール、クラス、または構造体、またはプロシージャではなく元のファイルまたは名前空間には、パブリックの要素を宣言することができます。  
  
## <a name="protected"></a>プロテクト  
 [Protected](../../../../visual-basic/language-reference/modifiers/protected.md)宣言ステートメントのキーワードは、同じクラス内またはこのクラスから派生したクラスから、要素をからのみアクセスできることを指定します。 次のコードはサンプル`Protected`宣言します。  
  
```vb  
Protected Class classForMyHeirs  
```  
  
 使用することができます`Protected`クラスでのみレベル、およびのみ宣言する場合、クラスのメンバー。 つまり、元のファイルまたは名前空間、またはインターフェイス、モジュール、構造体、またはプロシージャ内のレベルではなくが、クラスでは、保護されている要素を宣言することができます。  
  
## <a name="friend"></a>Friend  
 [フレンド](../../../../visual-basic/language-reference/modifiers/friend.md)宣言ステートメントでキーワードは、同じアセンブリ内からは、要素をからアクセスできることを指定します、アセンブリ外です。 次のコードはサンプル`Friend`宣言します。  
  
```vb  
Friend stringForThisProject As String  
```  
  
 使用することができます`Friend`モジュール、インターフェイス、または名前空間レベルでのみです。 これは、フレンド要素は、レベル内で、インターフェイス、モジュール、クラス、または構造体、またはプロシージャではなく元のファイルまたは名前空間を宣言することを意味します。  
  
## <a name="protected-friend"></a>保護されたフレンド  
 [Protected Friend](../../../language-reference/modifiers/protected-friend.md)宣言ステートメントでキーワードの組み合わせでは、派生クラスから、または内から、要素にアクセスできることを指定します、同じアセンブリまたはその両方です。 次のコードはサンプル`Protected Friend`宣言します。  
  
```vb  
Protected Friend stringForProjectAndHeirs As String  
```  
  
 使用することができます`Protected Friend`クラスでのみレベル、およびのみ宣言する場合、クラスのメンバー。 つまり、元のファイルまたは名前空間、またはインターフェイス、モジュール、構造体、またはプロシージャ内のレベルではなくが、クラスでは、保護されたフレンド要素を宣言することができます。  
  
## <a name="private"></a>Private  
 [プライベート](../../../../visual-basic/language-reference/modifiers/private.md)宣言ステートメントのキーワードは、モジュール、クラスまたは構造内からのみ、要素にアクセスできることを指定します。 次のコードはサンプル`Private`宣言します。  
  
```vb  
Private numberForMeOnly As Integer  
```  
  
 `Private` は、モジュール レベルでのみ使用できます。 つまり、モジュール、クラス、または構造体の内部が元のファイルまたは名前空間、インターフェイス内またはプロシージャ レベルではなくプライベート要素を宣言することができます。  
  
 モジュール レベルでも、`Dim`アクセス レベル キーワードを指定せず、ステートメントは等価を`Private`宣言します。 使用するただし、`Private`コードを読みやすくキーワード。  

## <a name="private-protected"></a>Private Protected

[Private Protected](../../../language-reference/modifiers/private-protected.md)宣言ステートメントでキーワードの組み合わせは、同じクラス内だけでなく、包含クラスと同じアセンブリ内にある派生クラス、要素をからのみアクセスできることを指定します。 `Private Protected`アクセス修飾子は Visual Basic 15.5 以降でサポートされています。

次の例は、`Private Protected`宣言。

```vb
Private Protected internalValue As Integer
```

宣言することができます、`Private Protected`クラスの内部でのみの要素。 構造体、またはインターフェイス内で宣言することはできません。 またできますとして宣言するソース ファイルまたは名前空間、インターフェイスまたは構造体の内部またはプロシージャ内のレベルで。

`Private Protected`アクセス修飾子は Visual Basic 15.5 以降でサポートされています。 これを使用するには、Visual Basic プロジェクト (*.vbproj) ファイルに次の要素を追加します。 Visual Basic 15.5 いる限り、またはそれ以降は、システムにインストールされているが、最新バージョンの Visual Basic コンパイラでサポートされているすべての言語機能を活用することができます。

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

使用する、`Private Protected`アクセス修飾子は、Visual Basic プロジェクト (*.vbproj) ファイルに次の要素を追加する必要があります。

```xml
<PropertyGroup>
   <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

詳細については、次を参照してください。 [Visual Basic の言語バージョンを設定](../../../language-reference/configure-language-version.md)します。

## <a name="access-modifiers"></a>アクセス修飾子  

アクセス レベルを指定するキーワードが呼び出される*アクセス修飾子*します。 次の表は、アクセス修飾子を比較します。  
  
|アクセス修飾子|付与されるアクセス レベル|要素がこのアクセス レベルを宣言することができます。|宣言のコンテキストをこの修飾子を使用することができます。|  
|---------------------|--------------------------|-----------------------------------------------------|----------------------------------------------------------------|  
|`Public`|無制限の。<br /><br /> パブリック要素を参照できる任意のコードがアクセスできます。|インターフェイス<br /><br /> モジュール<br /><br /> クラス<br /><br /> 構造体<br /><br /> 構造体のメンバー<br /><br /> 手順<br /><br /> プロパティ<br /><br /> メンバー変数<br /><br /> 定数<br /><br /> 列挙<br /><br /> イベント<br /><br /> 外部宣言<br /><br /> デリゲート|ソース ファイル<br /><br /> 名前空間<br /><br /> Interface<br /><br /> Module<br /><br /> クラス<br /><br /> 構造体|  
|`Protected`|継承。<br /><br /> 要素にアクセスできる、保護されている要素、またはそれから派生したクラスを宣言するクラス内のコードします。|インターフェイス<br /><br /> クラス<br /><br /> 構造体<br /><br /> 手順<br /><br /> プロパティ<br /><br /> メンバー変数<br /><br /> 定数<br /><br /> 列挙<br /><br /> イベント<br /><br /> 外部宣言<br /><br /> デリゲート|クラス|  
|`Friend`|アセンブリ:<br /><br /> フレンド要素がアクセスできる宣言アセンブリ内のコードします。|インターフェイス<br /><br /> モジュール<br /><br /> クラス<br /><br /> 構造体<br /><br /> 構造体のメンバー<br /><br /> 手順<br /><br /> プロパティ<br /><br /> メンバー変数<br /><br /> 定数<br /><br /> 列挙<br /><br /> イベント<br /><br /> 外部宣言<br /><br /> デリゲート|ソース ファイル<br /><br /> 名前空間<br /><br /> Interface<br /><br /> Module<br /><br /> クラス<br /><br /> 構造体|  
|`Protected` `Friend`|共用体の`Protected`と`Friend`:<br /><br /> 同じクラスまたは保護されたフレンド要素または要素のクラスから派生したクラス内では、同じアセンブリのコードは、アクセスできます。|インターフェイス<br /><br /> クラス<br /><br /> 構造体<br /><br /> 手順<br /><br /> プロパティ<br /><br /> メンバー変数<br /><br /> 定数<br /><br /> 列挙<br /><br /> イベント<br /><br /> 外部宣言<br /><br /> デリゲート|クラス|  
|`Private`|宣言コンテキスト:<br /><br /> コード内に含まれる型は、コードを含め、プライベートの要素を宣言する型の要素にアクセスできます。|インターフェイス<br /><br /> クラス<br /><br /> 構造体<br /><br /> 構造体のメンバー<br /><br /> 手順<br /><br /> プロパティ<br /><br /> メンバー変数<br /><br /> 定数<br /><br /> 列挙<br /><br /> イベント<br /><br /> 外部宣言<br /><br /> デリゲート|Module<br /><br /> クラス<br /><br /> 構造体|
|`Private Protected`|秘密の保護されている要素を宣言するクラスのコードまたは bas クラスと同じアセンブリ内にある派生クラスでのコード。|インターフェイス<br /><br /> クラス<br /><br /> 構造体<br /><br /> 手順<br /><br /> プロパティ<br /><br /> メンバー変数<br /><br /> 定数<br /><br /> 列挙<br /><br /> イベント<br /><br /> 外部宣言<br /><br /> デリゲート|クラス|
  
## <a name="see-also"></a>関連項目

- [Dim ステートメント](../../../../visual-basic/language-reference/statements/dim-statement.md)
- [Static](../../../../visual-basic/language-reference/modifiers/static.md)
- [宣言された要素の名前](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [宣言された要素の参照](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [宣言された要素の特性](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [Visual Basic での有効期間](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [Visual Basic におけるスコープ](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [方法: コントロール変数の可用性](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-availability-of-a-variable.md)
- [変数](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [変数宣言](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
