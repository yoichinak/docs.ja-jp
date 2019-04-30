---
title: My.Settings オブジェクト (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.MySettingsProperty.Settings
- My.Settings
helpviewer_keywords:
- My.Settings object
ms.assetid: 41f30dc1-202a-4273-b9b7-5728941f996c
ms.openlocfilehash: a962f7cce961b1ee6829702a6815ba02c534efb4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62050312"
---
# <a name="mysettings-object"></a>My.Settings オブジェクト
プロパティと、アプリケーションの設定にアクセスするためのメソッドを提供します。  
  
## <a name="remarks"></a>Remarks  
 `My.Settings`オブジェクトは、アプリケーションの設定へのアクセスを提供し、動的に格納し、プロパティの設定と、アプリケーションの他の情報を取得することができます。 詳細については、「[アプリケーションの設定の管理 (.NET)](/visualstudio/ide/managing-application-settings-dotnet)」を参照してください。  
  
## <a name="properties"></a>プロパティ  
 `My.Settings` オブジェクトのプロパティを使用すると、アプリケーションの設定にアクセスできます。 を追加または削除の設定を使用して、**設定デザイナー**します。  
  
 各設定は、**名前**、**型**、**スコープ**と**値**、これらの設定を確認する方法各設定にアクセスするプロパティ表示されます、`My.Settings`オブジェクト。  
  
- **名前**プロパティの名前を指定します。  
  
- **型**プロパティの種類を決定します。  
  
- **スコープ**プロパティは読み取り専用のかどうかを示します。 値が場合**アプリケーション**、プロパティは読み取り専用です。 値の場合**ユーザー**、プロパティが読み取り/書き込みです。  
  
- **値**はプロパティの既定値です。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|---|---|  
|`Reload`|最後に保存されている値からユーザーの設定を再読み込みします。|  
|`Save`|現在のユーザー設定を保存します。|  
  
 `My.Settings`オブジェクトは、高度なプロパティとから継承されたメソッドにも提供します、<xref:System.Configuration.ApplicationSettingsBase>クラス。  
  
## <a name="tasks"></a>[タスク]  
 次の表に、関連するタスクの例については、`My.Settings`オブジェクト。  
  
|目的|参照トピック|  
|---|---|  
|アプリケーション設定を読み取り|[方法: Visual Basic でアプリケーション設定を読み取る](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)|  
|ユーザー設定を変更します。|[方法: Visual Basic でユーザー設定を変更する](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)|  
|ユーザー設定します。|[方法: Visual Basic でユーザー設定を永続化する](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)|  
|ユーザー設定のプロパティ グリッドを作成します。|[方法: Visual Basic でユーザー設定のためのプロパティ グリッドを作成する](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)|  
  
## <a name="example"></a>例  
 次の例は、`Nickname` の設定値を表示します。  
  
 [!code-vb[VbVbalrMyResources#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#14)]  
  
 この例を実行するには、アプリケーションで `String` 型の `Nickname` を設定する必要があります。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Configuration.ApplicationSettingsBase>
- [方法: Visual Basic でアプリケーション設定を読み取る](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [方法: Visual Basic でユーザー設定を変更する](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [方法: Visual Basic でユーザー設定を永続化する](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [方法: Visual Basic でユーザー設定のためのプロパティ グリッドを作成する](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [アプリケーションの設定の管理 (.NET)](/visualstudio/ide/managing-application-settings-dotnet)
