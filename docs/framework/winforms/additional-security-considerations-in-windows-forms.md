---
title: Windows フォームのセキュリティに関するその他の考慮事項
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, secure calls to Windows API
- security [Windows Forms]
- security [Windows Forms], calling APIs
- Clipboard [Windows Forms], securing access
ms.assetid: 15abda8b-0527-47c7-aedb-77ab595f2bf1
ms.openlocfilehash: a101b5838b843f0130d16aab6eb199c7a54ca6b9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61669317"
---
# <a name="additional-security-considerations-in-windows-forms"></a>Windows フォームのセキュリティに関するその他の考慮事項
[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] セキュリティ設定によっては、ローカル コンピューターとは異なり、アプリケーションが部分信頼環境で実行されることがあります。 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] は、ファイル システム、ネットワーク、アンマネージ API などの重要なローカル リソースへのアクセスを他のリソースの場合よりも制限します。 セキュリティ設定では、Microsoft Windows API またはその他のセキュリティ システムで検証できない Api を呼び出す機能に影響します。 また、ファイルやデータへのアクセス、印刷など、アプリケーションのその他の処理にも影響があります。 部分信頼環境でのファイルやデータへのアクセスの詳細については、「[Windows フォームにおけるファイルおよびデータへのより安全なアクセス](more-secure-file-and-data-access-in-windows-forms.md)」を参照してください。 部分信頼環境での印刷の詳細については、「[Windows フォームでのより安全な印刷](more-secure-printing-in-windows-forms.md)」を参照してください。  
  
 次のセクションでは、クリップボードの使用、ウィンドウ操作の実行、および部分信頼環境で実行されているアプリケーションから Windows API を呼び出す方法について説明します。  
  
## <a name="clipboard-access"></a>クリップボードへのアクセス  
 <xref:System.Security.Permissions.UIPermission>クラスは、クリップボードと関連付けられているへのアクセスを制御<xref:System.Security.Permissions.UIPermissionClipboard>列挙値は、アクセスのレベルを示します。 使用されるアクセス許可レベルを次の表に示します。  
  
|UIPermissionClipboard の値|説明|  
|---------------------------------|-----------------|  
|<xref:System.Security.Permissions.UIPermissionClipboard.AllClipboard>|クリップボードは制限なしに使用できます。|  
|<xref:System.Security.Permissions.UIPermissionClipboard.OwnClipboard>|クリップボードは制限付きで使用できます。 クリップボードにデータを格納する機能 ([コピー] または [切り取り] のコマンド操作) は制限されません。 テキスト ボックスなど、[貼り付け] を受け入れる固有のコントロールは、クリップボードのデータを受け入れます。しかし、ユーザー コントロールはプログラムでクリップボードからデータを読み取ることができません。|  
|<xref:System.Security.Permissions.UIPermissionClipboard.NoClipboard>|クリップボードは使用できません。|  
  
 ローカル イントラネット ゾーンでは既定では、<xref:System.Security.Permissions.UIPermissionClipboard.AllClipboard>アクセスと、インターネット ゾーンを受け取る<xref:System.Security.Permissions.UIPermissionClipboard.OwnClipboard>アクセスします。 つまり、アプリケーションはクリップボードにデータをコピーできますが、プログラムでクリップボードに貼り付けたりクリップボードから読み取ったりはできません。 これらの制限により、完全に信頼されていないプログラムは、他のアプリケーションによってクリップボードにコピーされた内容を読み取ることができません。 アプリケーションがクリップボードへの完全なアクセスを必要とするにもかかわらず、アクセス許可がない場合は、アプリケーションに対するアクセス許可を昇格する必要があります。 アクセス許可の昇格の詳細については、「[一般的なセキュリティ ポリシー管理](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ed5htz45(v=vs.100))」を参照してください。  
  
## <a name="window-manipulation"></a>ウィンドウ操作  
 <xref:System.Security.Permissions.UIPermission>クラスもウィンドウ操作と、他の UI 関連のアクションと関連付けられているを実行するアクセス許可を制御<xref:System.Security.Permissions.UIPermissionWindow>列挙値は、アクセスのレベルを示します。 使用されるアクセス許可レベルを次の表に示します。  
  
 ローカル イントラネット ゾーンでは既定では、<xref:System.Security.Permissions.UIPermissionWindow.AllWindows>アクセスと、インターネット ゾーンを受け取る<xref:System.Security.Permissions.UIPermissionWindow.SafeTopLevelWindows>アクセスします。 つまり、[インターネット] ゾーンでは、アプリケーションがほとんどのウィンドウ操作および UI 関連処理を実行できますが、ウィンドウの外観が変更されます。 変更されたウィンドウには、最初の実行時にバルーン通知が表示され、変更されたタイトル バー テキストが表示され、タイトル バーに閉じるボタンが必要になります。 バルーン通知とタイトル バーは、アプリケーションのユーザーに、アプリケーションが部分信頼で動作していることを示します。  
  
|UIPermissionWindow の値|説明|  
|------------------------------|-----------------|  
|<xref:System.Security.Permissions.UIPermissionWindow.AllWindows>|ユーザーは、すべてのウィンドウとユーザー入力イベントを無制限に使用できます。|  
|<xref:System.Security.Permissions.UIPermissionWindow.SafeTopLevelWindows>|ユーザーは、セーフ トップレベル ウィンドウとセーフ サブウィンドウだけを描画に使用でき、それらのセーフ トップレベル ウィンドウとセーフ サブウィンドウの中のユーザー インターフェイスに対するユーザー入力イベントだけを使用できます。 これらのセーフ ウィンドウには明確なラベルが付けられ、最小サイズと最大サイズに制限があります。 制限システム ログオン画面やシステムのデスクトップの偽装などの問題を引き起こす可能性のスプーフィング攻撃を防止し、ウィンドウや、フォーカスに関連する Api の使用を親にプログラムでアクセスを制限、<xref:System.Windows.Forms.ToolTip>コントロール|  
|<xref:System.Security.Permissions.UIPermissionWindow.SafeSubWindows>|ユーザーは、セーフ サブウィンドウだけを描画に使用でき、そのセーフ サブウィンドウの中のユーザー インターフェイスに対するユーザー入力イベントだけを使用できます。 ブラウザー内に表示されるコントロールは、セーフ サブウィンドウの一例です。|  
|<xref:System.Security.Permissions.UIPermissionWindow.NoWindows>|ユーザーは、ウィンドウおよびユーザー インターフェイス イベントを使用できません。 ユーザー インターフェイスは使用できません。|  
  
 各アクセス許可のレベルで識別される、<xref:System.Security.Permissions.UIPermissionWindow>列挙体は、その上のレベルよりも少ない操作を許可します。 次の表は、によって制限される操作を示す、<xref:System.Security.Permissions.UIPermissionWindow.SafeTopLevelWindows>と<xref:System.Security.Permissions.UIPermissionWindow.SafeSubWindows>値。 各メンバーに対して必要なアクセス許可については、.NET Framework クラス ライブラリのドキュメントで該当するメンバーのトピックを参照してください。  
  
 <xref:System.Security.Permissions.UIPermissionWindow.SafeTopLevelWindows> アクセス許可は、次の表に示す操作を制限します。  
  
|コンポーネント|制限される処理|  
|---------------|------------------------|  
|<xref:System.Windows.Forms.Application>|-   <xref:System.Windows.Forms.Application.SafeTopLevelCaptionFormat%2A> プロパティの設定|  
|<xref:System.Windows.Forms.Control>|Getting、<xref:System.Windows.Forms.Control.Parent%2A>プロパティ。<br />-   `Region` プロパティの設定<br />-呼び出し、 <xref:System.Windows.Forms.Control.FindForm%2A> 、 <xref:System.Windows.Forms.Control.Focus%2A>、<xref:System.Windows.Forms.Control.FromChildHandle%2A>と<xref:System.Windows.Forms.Control.FromHandle%2A>、 <xref:System.Windows.Forms.Control.PreProcessMessage%2A>、 <xref:System.Windows.Forms.Control.ReflectMessage%2A>、または<xref:System.Windows.Forms.Control.SetTopLevel%2A>メソッド。<br />-呼び出し、<xref:System.Windows.Forms.Control.GetChildAtPoint%2A>メソッド、制御が返された場合は、呼び出し元コントロールの子ではありません。<br />-   コンテナー コントロール内でのコントロール フォーカスの変更|  
|<xref:System.Windows.Forms.Cursor>|-   <xref:System.Windows.Forms.Cursor.Clip%2A> プロパティの設定<br />-呼び出し、<xref:System.Windows.Forms.Control.Hide%2A>メソッド。|  
|<xref:System.Windows.Forms.DataGrid>|-呼び出し、<xref:System.Windows.Forms.ContainerControl.ProcessTabKey%2A>メソッド。|  
|<xref:System.Windows.Forms.Form>|Getting、<xref:System.Windows.Forms.Form.ActiveForm%2A>または<xref:System.Windows.Forms.Form.MdiParent%2A>プロパティ。<br />-設定、 <xref:System.Windows.Forms.Form.ControlBox%2A>、 <xref:System.Windows.Forms.Form.ShowInTaskbar%2A>、または<xref:System.Windows.Forms.Form.TopMost%2A>プロパティ。<br />-設定、 <xref:System.Windows.Forms.Form.Opacity%2A> 50% を下回るプロパティ。<br />-設定、<xref:System.Windows.Forms.Form.WindowState%2A>プロパティを<xref:System.Windows.Forms.FormWindowState.Minimized>プログラムを使用します。<br />-呼び出し、<xref:System.Windows.Forms.Form.Activate%2A>メソッド。<br />-を使用して、 <xref:System.Windows.Forms.FormBorderStyle.None>、 <xref:System.Windows.Forms.FormBorderStyle.FixedToolWindow>、および<xref:System.Windows.Forms.FormBorderStyle.SizableToolWindow><xref:System.Windows.Forms.FormBorderStyle>列挙値。|  
|<xref:System.Windows.Forms.NotifyIcon>|-を使用して、<xref:System.Windows.Forms.NotifyIcon>コンポーネントは完全に制限されています。|  
  
 <xref:System.Security.Permissions.UIPermissionWindow.SafeSubWindows>値による制限をさらに、次の表に示す操作を制限する、<xref:System.Security.Permissions.UIPermissionWindow.SafeTopLevelWindows>値。  
  
|コンポーネント|制限される処理|  
|---------------|------------------------|  
|<xref:System.Windows.Forms.CommonDialog>|-派生したダイアログ ボックスを表示、<xref:System.Windows.Forms.CommonDialog>クラス。|  
|<xref:System.Windows.Forms.Control>|-呼び出し、<xref:System.Windows.Forms.Control.CreateGraphics%2A>メソッド。<br />-   <xref:System.Windows.Forms.Control.Cursor%2A> プロパティの設定|  
|<xref:System.Windows.Forms.Control.Cursor%2A>|-   <xref:System.Windows.Forms.Cursor.Current%2A> プロパティの設定|  
|<xref:System.Windows.Forms.MessageBox>|-呼び出し、<xref:System.Windows.Forms.Form.Show%2A>メソッド。|  
  
### <a name="hosting-third-party-controls"></a>サードパーティ コントロールのホスト  
 フォームでサードパーティ コントロールをホストしている場合、他の種類のウィンドウ操作が発生する可能性があります。 サード パーティ製のコントロールが任意のカスタム<xref:System.Windows.Forms.UserControl>されませんが開発され、自分でコンパイルします。 ホスト シナリオを攻略するのは困難ですが、理論上、サードパーティ コントロールが描画サーフェイスを拡張して、フォームの領域全体を対象にする可能性があります。 このようなコントロールは、重要なダイアログ ボックスを模倣し、ユーザーのユーザー名/パスワードの組み合わせや銀行口座番号などの情報を要求する可能性があります。  
  
 このような考えられるリスクを制限するために、信頼できる販売元のサードパーティ コントロールのみを使用します。 確認できないソースからサードパーティ コントロールをダウンロードした場合、攻略行為が実行されないかソース コードを確認することをお勧めします。 ソースに悪意がないことを検証してから、アセンブリを自分でコンパイルし、ソースがアセンブリと一致することを確認します。  
  
## <a name="windows-api-calls"></a>Windows API の呼び出し  
 アプリケーションの設計では、Windows API から関数を呼び出す必要がある場合、アンマネージ コードにアクセスしています。 この場合、Windows API の呼び出しまたは値を使用しているときに、ウィンドウまたはオペレーティング システムに、コードの動作が決定ことはできません。 <xref:System.Security.Permissions.SecurityPermission>クラスおよび<xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode>の値、<xref:System.Security.Permissions.SecurityPermissionFlag>列挙体は、アンマネージ コードへのアクセスを制御します。 アプリケーションは、与えられている場合にのみアンマネージ コードにアクセスできる、<xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode>権限。 既定では、ローカルで実行されているアプリケーションだけがアンマネージ コードを呼び出すことができます。  
  
 Windows フォームの一部のメンバーを必要とするアンマネージ アクセスを提供する、<xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode>権限。 次の表に、内のメンバー、<xref:System.Windows.Forms>名前空間アクセス許可が必要です。 メンバーに対して必要なアクセス許可の詳細については、.NET Framework クラス ライブラリのドキュメントを参照してください。  
  
|コンポーネント|メンバー|  
|---------------|------------|  
|<xref:System.Windows.Forms.Application>|-   <xref:System.Windows.Forms.Application.AddMessageFilter%2A> メソッド<br />-   <xref:System.Windows.Forms.Application.CurrentInputLanguage%2A> プロパティ<br />-   `Exit` メソッド<br />-   <xref:System.Windows.Forms.Application.ExitThread%2A> メソッド<br />-   <xref:System.Windows.Forms.Application.ThreadException> イベント|  
|<xref:System.Windows.Forms.CommonDialog>|-   <xref:System.Windows.Forms.CommonDialog.HookProc%2A> メソッド<br />-   <xref:System.Windows.Forms.CommonDialog.OwnerWndProc%2A>\ メソッド<br />-   <xref:System.Windows.Forms.CommonDialog.Reset%2A> メソッド<br />-   <xref:System.Windows.Forms.CommonDialog.RunDialog%2A> メソッド|  
|<xref:System.Windows.Forms.Control>|-   <xref:System.Windows.Forms.Control.CreateParams%2A> メソッド<br />-   <xref:System.Windows.Forms.Control.DefWndProc%2A> メソッド<br />-   <xref:System.Windows.Forms.Control.DestroyHandle%2A> メソッド<br />-   <xref:System.Windows.Forms.Control.WndProc%2A> メソッド|  
|<xref:System.Windows.Forms.Help>|-   <xref:System.Windows.Forms.Help.ShowHelp%2A> メソッド<br />-   <xref:System.Windows.Forms.Help.ShowHelpIndex%2A> メソッド|  
|<xref:System.Windows.Forms.NativeWindow>|-   <xref:System.Windows.Forms.NativeWindow> クラス|  
|<xref:System.Windows.Forms.Screen>|-   <xref:System.Windows.Forms.Screen.FromHandle%2A> メソッド|  
|<xref:System.Windows.Forms.SendKeys>|-   <xref:System.Windows.Forms.SendKeys.Send%2A> メソッド<br />-   <xref:System.Windows.Forms.SendKeys.SendWait%2A> メソッド|  
  
 アプリケーションを要求する必要があるかどうか、アプリケーションにはアンマネージ コードを呼び出すアクセス許可はありません、<xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode>権限、または別の機能を実装する方法を検討する必要があります。 多くの場合、Windows フォームが Windows を管理対象の代替手段を提供します。API 関数。 代わりの手段がなく、アプリケーションがアンマネージ コードにアクセスする必要がある場合は、アプリケーションに対するアクセス許可を昇格する必要があります。  
  
 アンマネージ コードを呼び出すアクセス許可を与えられたアプリケーションは、ほとんどの処理を実行できます。 そのため、アンマネージ コードを呼び出すアクセス許可は、信頼されたソースからのアプリケーションに対してだけ与えるようにしてください。 また、アプリケーションによっては、アンマネージ コードの呼び出しを生成するアプリケーション機能の一部をオプションにするか、完全に信頼された環境でのみ有効にすることもできます。 危険なアクセス許可の詳細については、「[危険なアクセス許可とポリシー管理](../misc/dangerous-permissions-and-policy-administration.md)」を参照してください。 アクセス許可の昇格の詳細については、「[一般的なセキュリティ ポリシー管理](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ed5htz45(v=vs.100))」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [Windows フォームにおけるファイルおよびデータへのより安全なアクセス](more-secure-file-and-data-access-in-windows-forms.md)
- [Windows フォームでのより安全な印刷](more-secure-printing-in-windows-forms.md)
- [Windows フォームのセキュリティの概要](security-in-windows-forms-overview.md)
- [Windows フォームのセキュリティ](windows-forms-security.md)
- [ClickOnce アプリケーションのセキュリティ](/visualstudio/deployment/securing-clickonce-applications)
