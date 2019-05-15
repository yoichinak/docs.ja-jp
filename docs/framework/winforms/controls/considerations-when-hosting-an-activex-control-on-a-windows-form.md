---
title: Windows フォームで ActiveX コントロールをホストする場合の考慮事項
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, ActiveX controls
- ActiveX controls [Windows Forms], hosting
- Windows Forms, ActiveX controls
- Windows Forms, hosting ActiveX controls
- ActiveX controls [Windows Forms], adding
ms.assetid: 2509302d-a74e-484f-9890-2acdbfa67a68
ms.openlocfilehash: 4b604502e0fea591460f30cae28b64ff1703da65
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2019
ms.locfileid: "65589441"
---
# <a name="considerations-when-hosting-an-activex-control-on-a-windows-form"></a>Windows フォームで ActiveX コントロールをホストする場合の考慮事項
Windows フォームは、Windows フォーム コントロールをホストするために最適化されていますが、ActiveX コントロールを使うこともできます。 ActiveX コントロールを使うアプリケーションを計画するときは、次の考慮事項に留意してください。  
  
- **セキュリティ** 共通言語ランタイムは、コード アクセス セキュリティに関して強化されました。 Windows フォームを使うアプリケーションは、完全に信頼された環境では問題なく動作し、信頼性が高くない環境ではほとんどの機能がアクセス可能な状態で動作します。 Windows フォーム コントロールは、ブラウザーで問題なくホストできます。 ただし、Windows フォームの ActiveX コントロールは、これらのセキュリティ強化を利用できません。 ActiveX コントロールを実行するには、アンマネージ コード アクセス許可が設定されている必要があります、<xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A?displayProperty=nameWithType>プロパティ。 セキュリティとアンマネージ コード アクセス許可の詳細については、次を参照してください。<xref:System.Security.Permissions.SecurityPermissionAttribute>します。  
  
- **総保有コスト** Windows フォームに追加される ActiveX コントロールは、その Windows フォーム全体と共に配置されるため、作成されるファイルのサイズが大幅に追加する可能性があります。 さらに、Windows フォームで ActiveX コントロールを使うには、レジストリへの書き込みが必要です。 これは、レジストリへの書き込みを必要としない Windows フォーム コントロールと比較して、ユーザーのコンピューターに大きく干渉します。  
  
    > [!NOTE]
    >  ActiveX コントロールを操作するには、COM 相互運用ラッパーを使う必要があります。 詳しくは、「[Visual Basic および Visual C# における COM 相互運用性](~/docs/visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)」をご覧ください。  
  
    > [!NOTE]
    >  ActiveX コントロールのメンバーの名前が、.NET Framework で定義された名前と一致するかどうかは、ActiveX コントロール インポーターは、メンバー名をプレフィックス**Ctl**作成時、<xref:System.Windows.Forms.AxHost>クラスを派生します。 たとえば、ActiveX コントロールがあるという名前のメンバー**レイアウト**、名前が変更**CtlLayout** 、AxHost 派生クラスでため、**レイアウト**内でイベントが定義されている、します。NET Framework。  
  
## <a name="see-also"></a>関連項目

- [方法: Windows フォームに ActiveX コントロールを追加します。](how-to-add-activex-controls-to-windows-forms.md)
- [コード アクセス セキュリティ](../../misc/code-access-security.md)
- [各言語およびライブラリにおける、コントロールとプログラミング可能オブジェクトの比較](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0061wezk(v=vs.100))
- [Windows フォームへのコントロールの追加](putting-controls-on-windows-forms.md)
- [Windows フォーム コントロール](index.md)
