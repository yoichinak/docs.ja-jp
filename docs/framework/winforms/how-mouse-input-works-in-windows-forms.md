---
title: Windows フォームにおけるマウス入力のしくみ
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, mouse input
- mouse [Windows Forms], input
ms.assetid: 48fc5240-75a6-44bf-9fce-6aa21b49705a
ms.openlocfilehash: c9193ffa9ef34f1e43a92feec230fa2282264147
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59203016"
---
# <a name="how-mouse-input-works-in-windows-forms"></a>Windows フォームにおけるマウス入力のしくみ
マウス入力の処理を受け取って、すべての Windows アプリケーションの重要な部分です。 アプリケーションでは、操作を実行するマウス イベントを処理したり、ヒット テストを実行するマウスの位置情報やその他のアクションを使用できます。 さらに、アプリケーションでは、コントロールがマウス入力を処理する方法を変更することができます。 このトピックでは、これらのマウス イベントの詳細と、取得して、マウスのシステム設定を変更する方法について説明します。 イベントと、マウスのクリック イベントを注文の発生をマウスで提供されるデータの詳細についてを参照してください[Windows フォームにおけるマウス イベント](mouse-events-in-windows-forms.md)します。  
  
## <a name="mouse-location-and-hit-testing"></a>マウスの位置とヒット テスト  
 マウスを移動すると、オペレーティング システムは、マウス ポインターを移動します。 マウス ポインターには、オペレーティング システムを追跡し、ポインターの位置として認識する、ホット スポットと呼ばれる、1 つのピクセルが含まれています。 ユーザーがマウスを移動または、マウス ボタンを押したとき、<xref:System.Windows.Forms.Control>を格納している、<xref:System.Windows.Forms.Cursor.HotSpot%2A>適切なマウス イベントを発生させます。 現在のマウスの位置を取得することができます、<xref:System.Windows.Forms.MouseEventArgs.Location%2A>のプロパティ、<xref:System.Windows.Forms.MouseEventArgs>マウス イベントを処理するときに、またはを使用して、<xref:System.Windows.Forms.Cursor.Position%2A>のプロパティ、<xref:System.Windows.Forms.Cursor>クラス。 その後マウスの位置情報を使用して、ヒット テストを実行しのマウスの位置に基づいてアクションを実行できます。 ヒット テストの機能に組み込まれている Windows フォームでのいくつかのコントロールなど、 <xref:System.Windows.Forms.ListView>、 <xref:System.Windows.Forms.TreeView>、<xref:System.Windows.Forms.MonthCalendar>と<xref:System.Windows.Forms.DataGridView>コントロール。 適切なマウス イベントと併用<xref:System.Windows.Forms.Control.MouseHover>など、ヒット テストは、アプリケーションが特定のアクションを実行する場合を決定するのに便利です。  
  
## <a name="mouse-events"></a>マウス イベント  
 マウスの入力に応答する主な方法では、マウス イベントを処理します。 次の表は、マウス イベントの表示し、が発生した場合について説明します。  
  
|マウス イベント|説明|  
|-----------------|-----------------|  
|<xref:System.Windows.Forms.Control.Click>|このイベントは、通常は前にマウス ボタンが離されたときに発生します。、<xref:System.Windows.Forms.Control.MouseUp>イベント。 このイベントのハンドラーは、型 <xref:System.EventArgs> の引数を受け取ります。 のみクリックが発生するかを判断する必要がある場合は、このイベントを処理します。|  
|<xref:System.Windows.Forms.Control.MouseClick>|このイベントは、ユーザーがマウスでコントロールをクリックしたときに発生します。 このイベントのハンドラーは、型 <xref:System.Windows.Forms.MouseEventArgs> の引数を受け取ります。 クリックが発生したときに、マウスに関する情報を取得する必要がある場合、このイベントを処理します。|  
|<xref:System.Windows.Forms.Control.DoubleClick>|このイベントは、コントロールがダブルクリックされたときに発生します。 このイベントのハンドラーは、型 <xref:System.EventArgs> の引数を受け取ります。 のみをダブルクリックした場合を判断する必要がある場合は、このイベントを処理します。|  
|<xref:System.Windows.Forms.Control.MouseDoubleClick>|このイベントは、ユーザーがマウスでコントロールをダブルクリックしたときに発生します。 このイベントのハンドラーは、型 <xref:System.Windows.Forms.MouseEventArgs> の引数を受け取ります。 ダブルクリックが発生したときに、マウスに関する情報を取得する必要がある場合、このイベントを処理します。|  
|<xref:System.Windows.Forms.Control.MouseDown>|このイベントは、コントロールの上にマウス ポインターが、マウス ボタンを押すと発生します。 このイベントのハンドラーは、型 <xref:System.Windows.Forms.MouseEventArgs> の引数を受け取ります。|  
|<xref:System.Windows.Forms.Control.MouseEnter>|このイベントは、マウス ポインターがコントロールの種類に応じて、コントロールの境界またはクライアントの領域に入ったときに発生します。 このイベントのハンドラーは、型 <xref:System.EventArgs> の引数を受け取ります。|  
|<xref:System.Windows.Forms.Control.MouseHover>|このイベントは、マウス ポインターが停止し、コントロールの上に置いたときに発生します。 このイベントのハンドラーは、型 <xref:System.EventArgs> の引数を受け取ります。|  
|<xref:System.Windows.Forms.Control.MouseLeave>|このイベントは、マウス ポインターがコントロールの種類に応じて、コントロールの境界またはクライアントの領域を離れるときに発生します。 このイベントのハンドラーは、型 <xref:System.EventArgs> の引数を受け取ります。|  
|<xref:System.Windows.Forms.Control.MouseMove>|このイベントは、コントロール上でマウス ポインターが移動したときに発生します。 このイベントのハンドラーは、型 <xref:System.Windows.Forms.MouseEventArgs> の引数を受け取ります。|  
|<xref:System.Windows.Forms.Control.MouseUp>|このイベントは、コントロールの上にマウス ポインターが、マウス ボタンを離すと発生します。 このイベントのハンドラーは、型 <xref:System.Windows.Forms.MouseEventArgs> の引数を受け取ります。|  
|<xref:System.Windows.Forms.Control.MouseWheel>|このイベントは、コントロールにフォーカスがあるユーザーがマウスのホイールを回転したときに発生します。 このイベントのハンドラーは、型 <xref:System.Windows.Forms.MouseEventArgs> の引数を受け取ります。 使用することができます、<xref:System.Windows.Forms.MouseEventArgs.Delta%2A>プロパティの<xref:System.Windows.Forms.MouseEventArgs>がマウスのスクロール量を決定します。|  
  
## <a name="changing-mouse-input-and-detecting-system-settings"></a>マウス入力を変更して、システム設定の検出  
 検出し、コントロール、コントロールからの派生を使用してマウス入力を処理する方法を変更することができます、<xref:System.Windows.Forms.Control.GetStyle%2A>と<xref:System.Windows.Forms.Control.SetStyle%2A>メソッド。 <xref:System.Windows.Forms.Control.SetStyle%2A>メソッドは、ビットごとの組み合わせ<xref:System.Windows.Forms.ControlStyles>コントロールがクリックしてまたはダブルクリック動作の標準を持つかどうか、またはコントロールがマウスの処理を処理するかどうかを判断する値。 さらに、<xref:System.Windows.Forms.SystemInformation>クラスには、マウスの機能について説明して、マウスがオペレーティング システムと対話する方法を指定するプロパティが含まれています。 次の表では、これらのプロパティをまとめたものです。  
  
|プロパティ|説明|  
|--------------|-----------------|  
|<xref:System.Windows.Forms.SystemInformation.DoubleClickSize%2A>|ピクセル単位でサイズを取得、ユーザーが 2 つの考慮すべきオペレーティング システムに対して 2 回クリックする必要があります、領域のクリックして、ダブルクリックします。|  
|<xref:System.Windows.Forms.SystemInformation.DoubleClickTime%2A>|最初のクリックと 2 番目のクリックをマウス操作がダブルクリックであるオペレーティング システムの間の経過時間をミリ秒単位の最大数を取得します。|  
|<xref:System.Windows.Forms.SystemInformation.MouseButtons%2A>|マウスのボタンの数を取得します。|  
|<xref:System.Windows.Forms.SystemInformation.MouseButtonsSwapped%2A>|左右のマウス ボタンの機能が入れ替わっているかどうかを示す値を取得します。|  
|<xref:System.Windows.Forms.SystemInformation.MouseHoverSize%2A>|マウス静止メッセージが生成されるためにマウス静止時間が経過するまでマウス ポインターをとどめておく必要がある四角形の領域のサイズ (ピクセル単位) を取得します。|  
|<xref:System.Windows.Forms.SystemInformation.MouseHoverTime%2A>|マウス静止メッセージが生成されるために静止領域内にマウス ポインターをとどめておく必要がある時間 (ミリ秒単位) を取得します。|  
|<xref:System.Windows.Forms.SystemInformation.MousePresent%2A>|マウスがインストールされているかどうかを示す値を取得します。|  
|<xref:System.Windows.Forms.SystemInformation.MouseSpeed%2A>|1 ~ 20、現在のマウス速度を示す値を取得します。|  
|<xref:System.Windows.Forms.SystemInformation.MouseWheelPresent%2A>|マウス ホイール付きのマウスが取り付けられているかどうかを示す値を取得します。|  
|<xref:System.Windows.Forms.SystemInformation.MouseWheelScrollDelta%2A>|1 つのマウス ホイールを回転の増分の差分値を取得します。|  
|<xref:System.Windows.Forms.SystemInformation.MouseWheelScrollLines%2A>|マウス ホイールを回転したときにスクロールする行数を取得します。|  
  
## <a name="see-also"></a>関連項目

- [Windows フォーム アプリケーションにおけるマウス入力](mouse-input-in-a-windows-forms-application.md)
- [Windows フォームにおけるマウスのキャプチャ](mouse-capture-in-windows-forms.md)
- [Windows フォームにおけるマウス ポインター](mouse-pointers-in-windows-forms.md)
