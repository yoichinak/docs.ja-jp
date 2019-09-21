---
title: My.forms オブジェクト (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.Forms
- My.MyProject.Forms
helpviewer_keywords:
- My.Forms object
ms.assetid: f6bff4e6-6769-4294-956b-037aa6106d2a
ms.openlocfilehash: 9fa5c77dd12c98100e3d17fc473a6802180d1e32
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965985"
---
# <a name="myforms-object"></a>My.Forms オブジェクト
現在のプロジェクトで宣言されている各 Windows フォームのインスタンスにアクセスするためのプロパティを提供します。  
  
## <a name="remarks"></a>Remarks  
 オブジェクト`My.Forms`は、現在のプロジェクトの各フォームのインスタンスを提供します。 プロパティの名前は、プロパティがアクセスするフォームの名前と同じです。   
  
 `My.Forms`オブジェクトによって提供されるフォームには、修飾子を付けずにフォームの名前を使用してアクセスできます。 プロパティ名はフォームの型名と同じであるため、既定のインスタンスがあるかのようにフォームにアクセスできます。 たとえば、`My.Forms.Form1.Show` は、`Form1.Show` と同じです。  
  
 オブジェクト`My.Forms`は、現在のプロジェクトに関連付けられているフォームのみを公開します。 参照先の Dll で宣言されたフォームへのアクセスを提供しません。 DLL が提供するフォームにアクセスするには、 *DllName*として記述されたフォームの修飾名を使用する必要があります。*FormName*。  
  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>プロパティを使用して、アプリケーションの開いているすべてのフォームのコレクションを取得できます。  
  
 オブジェクトとそのプロパティは、Windows アプリケーションでのみ使用できます。  
  
## <a name="properties"></a>プロパティ  
 `My.Forms`オブジェクトの各プロパティは、現在のプロジェクトのフォームのインスタンスへのアクセスを提供します。 プロパティの名前は、プロパティがアクセスするフォームの名前と同じであり、プロパティの型はフォームの型と同じです。  
  
> [!NOTE]
> 名前の競合がある場合、フォームにアクセスするためのプロパティ名は*RootNamespace*_*Namespace*\_*FormName*です。 たとえば`Form1.`、という名前の2つの形式を考えてみます。これらの形式のいずれかがルート名前空間`WindowsApplication1`にあり`My.Forms.WindowsApplication1_Namespace1_Form1`、名前空間`Namespace1`にある場合は、を使用してそのフォームにアクセスします。  
  
 `My.Forms`オブジェクトを使用すると、起動時に作成されたアプリケーションのメインフォームのインスタンスにアクセスできます。 その他のすべてのフォーム`My.Forms`では、オブジェクトは、アクセス時にフォームの新しいインスタンスを作成して格納します。 その後、そのプロパティにアクセスしようとすると、フォームのインスタンスが返されます。  
  
 フォームのプロパティにを割り当てる`Nothing`ことによって、フォームを破棄できます。 プロパティセッターは、フォーム<xref:System.Windows.Forms.Form.Close%2A>のメソッドを呼び出し、格納され`Nothing`ている値にを割り当てます。 以外`Nothing`の値をプロパティに割り当てた場合、setter は<xref:System.ArgumentException>例外をスローします。  
  
 `My.Forms`オブジェクトのプロパティが、 `Is`または`IsNot`演算子を使用してフォームのインスタンスを格納するかどうかをテストできます。 これらの演算子を使用すると、プロパティの値がで`Nothing`あるかどうかを確認できます。  
  
> [!NOTE]
> 通常、 `Is`または`IsNot`演算子は、比較を実行するためにプロパティの値を読み取る必要があります。 ただし、プロパティが現在を格納`Nothing`している場合、プロパティはフォームの新しいインスタンスを作成し、そのインスタンスを返します。 ただし、Visual Basic コンパイラは、 `My.Forms`オブジェクトのプロパティを異なる方法で処理し、または`IsNot`演算子が`Is`値を変更せずにプロパティの状態を確認できるようにします。  
  
## <a name="example"></a>例  
 この例では、既定`SidebarMenu`のフォームのタイトルを変更します。  
  
 [!code-vb[VbVbalrMyForms#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyForms/VB/Class1.vb#2)]  
  
 この例を使用するには、プロジェクトにという名前`SidebarMenu`のフォームが必要です。  
  
 このコードは、Windows アプリケーションプロジェクトでのみ機能します。  
  
## <a name="requirements"></a>必要条件  
  
### <a name="availability-by-project-type"></a>プロジェクトの種類別の可用性  
  
|プロジェクトの種類|使用可能|  
|---|---|  
|Windows アプリケーション|**はい**|  
|クラス ライブラリ|いいえ|  
|コンソール アプリケーション|いいえ|  
|Windows コントロールライブラリ|いいえ|  
|Web コントロールライブラリ|いいえ|  
|Windows サービス|いいえ|  
|Web サイト|いいえ|  
  
## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>
- <xref:System.Windows.Forms.Form>
- <xref:System.Windows.Forms.Form.Close%2A>
- [オブジェクト](../../../visual-basic/language-reference/objects/index.md)
- [Is 演算子](../../../visual-basic/language-reference/operators/is-operator.md)
- [IsNot 演算子](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [アプリケーション フォームへのアクセス](../../../visual-basic/developing-apps/programming/accessing-application-forms.md)
