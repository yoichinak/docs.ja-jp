---
title: My.Forms オブジェクト (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.Forms
- My.MyProject.Forms
helpviewer_keywords:
- My.Forms object
ms.assetid: f6bff4e6-6769-4294-956b-037aa6106d2a
ms.openlocfilehash: 4998097b910a504461a34af3cc159ddb1c74cc62
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58832555"
---
# <a name="myforms-object"></a>My.Forms オブジェクト
プロパティは、現在のプロジェクトで宣言されている各 Windows フォームのインスタンスへのアクセスを提供します。  
  
## <a name="remarks"></a>Remarks  
 `My.Forms`オブジェクトは、現在のプロジェクト内の各フォームのインスタンスを提供します。 プロパティの名前は、プロパティにアクセスするフォームの名前と同じです。   
  
 によって提供されるフォームへのアクセス、`My.Forms`修飾なしのフォームの名前を使用してオブジェクト。 プロパティ名は、フォームの型名と同じであるためこれにより、既定のインスタンスがあった場合、フォームにアクセスできます。 たとえば、`My.Forms.Form1.Show` は、`Form1.Show` と同じです。  
  
 `My.Forms`オブジェクトには、現在のプロジェクトに関連付けられているフォームのみが表示されます。 参照される Dll で宣言されているフォームへのアクセスは行いません。 DLL を提供するフォームにアクセスするには、ように、フォームの修飾名を使用する必要があります*DllName*.*FormName*します。  
  
 使用することができます、<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>プロパティをアプリケーションのすべてのオープン フォームのコレクションを取得します。  
  
 オブジェクトとそのプロパティは、Windows アプリケーションでのみ使用できます。  
  
## <a name="properties"></a>プロパティ  
 各プロパティ、`My.Forms`オブジェクトは、現在のプロジェクトのフォームのインスタンスへのアクセスを提供します。 プロパティの名前は、プロパティがアクセスすると、フォームの名前と同じとプロパティの型が、フォームの型と同じです。  
  
> [!NOTE]
>  フォームにアクセスするプロパティ名は、名前の競合がある場合*RootNamespace*_*Namespace*\_*FormName*します。 たとえば、という名前の 2 つの形式`Form1.`ルート名前空間ではこれらの形式のいずれかのかどうか`WindowsApplication1`と名前空間に`Namespace1`を通じてそのフォームをアクセスするには`My.Forms.WindowsApplication1_Namespace1_Form1`。  
  
 `My.Forms`オブジェクトが起動時に作成されたアプリケーションのメイン フォームのインスタンスへのアクセスを提供します。 その他のすべてのフォーム、`My.Forms`オブジェクトにアクセスし、格納する場合は、フォームの新しいインスタンスを作成します。 後続のプロパティにアクセスするは、フォームのインスタンスを返します。  
  
 割り当てることで、フォームを破棄することができます`Nothing`そのフォームのプロパティ。 プロパティ set アクセス操作子の呼び出し、<xref:System.Windows.Forms.Form.Close%2A>メソッドのフォーム、およびし割り当てます`Nothing`に格納されている値。 以外の任意の値を割り当てた場合`Nothing`プロパティの setter がスローされます、<xref:System.ArgumentException>例外。  
  
 プロパティかどうかをテストすることができます、`My.Forms`オブジェクトを使用して、フォームのインスタンスを格納する、`Is`または`IsNot`演算子。 これらの演算子を使用するには、プロパティの値をチェックする`Nothing`します。  
  
> [!NOTE]
>  通常、`Is`または`IsNot`オペレーターは、比較を実行するプロパティの値を読み取ることがあります。 ただし、プロパティが現在格納されている場合`Nothing`プロパティ、フォームの新しいインスタンスを作成し、し、そのインスタンスを返します。 ただし、Visual Basic コンパイラがのプロパティを処理、`My.Forms`でき、異なる方法でオブジェクト、`Is`または`IsNot`演算子をその値を変更することがなく、プロパティの状態を確認します。  
  
## <a name="example"></a>例  
 この例は、既定のタイトルを変更`SidebarMenu`フォーム。  
  
 [!code-vb[VbVbalrMyForms#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyForms/VB/Class1.vb#2)]  
  
 この例を動作させるには、プロジェクトがという名前のフォームをいる必要があります`SidebarMenu`します。  
  
 このコードは、Windows アプリケーション プロジェクトでのみ動作します。  
  
## <a name="requirements"></a>必要条件  
  
### <a name="availability-by-project-type"></a>プロジェクトの種類ごとの可用性  
  
|プロジェクトの種類|使用可能|  
|---|---|  
|Windows アプリケーション|**はい**|  
|クラス ライブラリ|いいえ|  
|コンソール アプリケーション|いいえ|  
|Windows コントロール ライブラリ|いいえ|  
|Web コントロール ライブラリ|いいえ|  
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
