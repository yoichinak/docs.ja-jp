---
title: My.forms オブジェクト (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.Forms
- My.MyProject.Forms
helpviewer_keywords:
- My.Forms object
ms.assetid: f6bff4e6-6769-4294-956b-037aa6106d2a
ms.openlocfilehash: 9a0b3b9202972122aea4a7147d8d872486418264
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581865"
---
# <a name="myforms-object"></a>My.Forms オブジェクト

現在のプロジェクトで宣言されている各 Windows フォームのインスタンスにアクセスするためのプロパティを提供します。

## <a name="remarks"></a>Remarks

@No__t_0 オブジェクトは、現在のプロジェクトの各フォームのインスタンスを提供します。 プロパティの名前は、プロパティがアクセスするフォームの名前と同じです。

@No__t_0 オブジェクトによって提供されるフォームには、修飾子を付けずにフォーム名を使用してアクセスできます。 プロパティ名はフォームの型名と同じであるため、既定のインスタンスがあるかのようにフォームにアクセスできます。 たとえば、`My.Forms.Form1.Show` は、`Form1.Show` と同じです。

@No__t_0 オブジェクトは、現在のプロジェクトに関連付けられているフォームのみを公開します。 参照先の Dll で宣言されたフォームへのアクセスを提供しません。 DLL が提供するフォームにアクセスするには、 *DllName*として記述されたフォームの修飾名を使用する必要があります。*FormName*。

@No__t_0 プロパティを使用して、すべてのアプリケーションの開いているフォームのコレクションを取得できます。

オブジェクトとそのプロパティは、Windows アプリケーションでのみ使用できます。

## <a name="properties"></a>プロパティ

@No__t_0 オブジェクトの各プロパティは、現在のプロジェクトのフォームのインスタンスへのアクセスを提供します。 プロパティの名前は、プロパティがアクセスするフォームの名前と同じであり、プロパティの型はフォームの型と同じです。

> [!NOTE]
> 名前の競合がある場合、フォームにアクセスするためのプロパティ名は*RootNamespace*_*Namespace* \_*FormName*になります。 たとえば、`Form1.`If という名前の2つのフォームがあるとします。これらの形式はルート名前空間 `WindowsApplication1`、名前空間 `Namespace1` では、`My.Forms.WindowsApplication1_Namespace1_Form1` 経由でそのフォームにアクセスします。

@No__t_0 オブジェクトを使用すると、起動時に作成されたアプリケーションのメインフォームのインスタンスにアクセスできます。 その他のすべてのフォームでは、`My.Forms` オブジェクトは、アクセス時にフォームの新しいインスタンスを作成して格納します。 その後、そのプロパティにアクセスしようとすると、フォームのインスタンスが返されます。

フォームのプロパティに `Nothing` を割り当てることによって、フォームを破棄できます。 プロパティ setter は、フォームの <xref:System.Windows.Forms.Form.Close%2A> メソッドを呼び出し、格納されている値に `Nothing` を割り当てます。 @No__t_0 以外の値をプロパティに割り当てた場合、setter は <xref:System.ArgumentException> 例外をスローします。

@No__t_1 または `IsNot` 演算子を使用して、`My.Forms` オブジェクトのプロパティがフォームのインスタンスを格納するかどうかをテストできます。 これらの演算子を使用すると、プロパティの値が `Nothing` かどうかを確認できます。

> [!NOTE]
> 通常、`Is` または `IsNot` 演算子は、比較を実行するためにプロパティの値を読み取る必要があります。 ただし、プロパティが現在 `Nothing` を格納している場合は、プロパティによってフォームの新しいインスタンスが作成され、そのインスタンスが返されます。 ただし、Visual Basic コンパイラは、`My.Forms` オブジェクトのプロパティを異なる方法で処理し、`Is` または `IsNot` の演算子が、値を変更せずにプロパティの状態を確認できるようにします。

## <a name="example"></a>例

この例では、既定の `SidebarMenu` フォームのタイトルを変更します。

[!code-vb[VbVbalrMyForms#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyForms/VB/Class1.vb#2)]

この例を使用するには、プロジェクトに `SidebarMenu` という名前のフォームが必要です。

このコードは、Windows アプリケーションプロジェクトでのみ機能します。

## <a name="requirements"></a>［要件］

### <a name="availability-by-project-type"></a>プロジェクトの種類別の可用性

|プロジェクトの種類|使用可能|
|---|---|
|Windows アプリケーション|**はい**|
|クラス ライブラリ|Ｘ|
|コンソール アプリケーション|Ｘ|
|Windows コントロールライブラリ|Ｘ|
|Web コントロールライブラリ|Ｘ|
|Windows サービス|Ｘ|
|Web サイト|Ｘ|

## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>
- <xref:System.Windows.Forms.Form>
- <xref:System.Windows.Forms.Form.Close%2A>
- [オブジェクト](../../../visual-basic/language-reference/objects/index.md)
- [Is 演算子](../../../visual-basic/language-reference/operators/is-operator.md)
- [IsNot 演算子](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [アプリケーション フォームへのアクセス](../../../visual-basic/developing-apps/programming/accessing-application-forms.md)
