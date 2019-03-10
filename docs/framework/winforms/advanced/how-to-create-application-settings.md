---
title: '方法: アプリケーション設定を作成します。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application settings [Windows Forms], Windows Forms
- application settings [Windows Forms], creating
ms.assetid: 1e7aa347-af75-41e5-89ca-f53cab704f72
ms.openlocfilehash: d540715c0b4c69b2981cc65f55b0fa950c5a4eaf
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57721243"
---
# <a name="how-to-create-application-settings"></a>方法: アプリケーション設定を作成します。
マネージド コードを使用することにより、新しいアプリケーション設定を作成し、フォームまたはフォームのコントロールのプロパティにバインドして、これらの設定が実行時に自動的に読み込まれて保存されるようにすることができます。  
  
 次の手順では、<xref:System.Configuration.ApplicationSettingsBase> から派生するラッパー クラスを手動で作成します。 このクラスには、公開する各アプリケーション設定に対して、パブリックにアクセスできるプロパティを追加します。  
  
 また、Visual Studio デザイナーで最小限のコードを使用してこの手順を実行することもできます。  参照してください[方法。デザイナーを使用してアプリケーション設定を作成する](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/wabtadw6(v=vs.100))します。  
  
### <a name="to-create-new-application-settings-programmatically"></a>新しいアプリケーション設定をプログラムで作成するには  
  
1.  プロジェクトに新しいクラスを追加して、名前を変更します。 この手順では、このクラスを呼び出し、`MyUserSettings`します。 クラスの派生元が <xref:System.Configuration.ApplicationSettingsBase> になるようクラス定義を変更します。  
  
2.  必要な各アプリケーション設定のこのラッパー クラスでプロパティを定義し、設定のスコープに応じて、そのプロパティを <xref:System.Configuration.ApplicationScopedSettingAttribute> または <xref:System.Configuration.UserScopedSettingAttribute> のいずれかを使用して適用します。 設定のスコープの詳細については、次を参照してください。[アプリケーション設定の概要](application-settings-overview.md)します。 ここまでで、コードは次のようになります。  
  
     [!code-csharp[ApplicationSettings.Create#1](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/MyAppSettings.cs#1)]
     [!code-vb[ApplicationSettings.Create#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/MyAppSettings.vb#1)]  
  
3.  アプリケーションでこのラッパー クラスのインスタンスを作成します。 これは、一般的にはメイン フォームのプライベート メンバーです。 クラスを定義したので、それをプロパティにバインドする必要があります。この場合は、フォームの <xref:System.Windows.Forms.Form.BackColor%2A> プロパティです。 これを実現するにはフォームの`Load`イベント ハンドラー。  
  
     [!code-csharp[ApplicationSettings.Create#2](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/Form1.cs#2)]
     [!code-vb[ApplicationSettings.Create#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/Form1.vb#2)]  
  
4.  実行時に設定を変更する方法を提供する場合は、フォームを閉じるときにユーザーの現在の設定をディスクに保存する必要があります。そうしないと、これらの変更が失われます。  
  
     [!code-csharp[ApplicationSettings.Create#3](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/Form1.cs#3)]
     [!code-vb[ApplicationSettings.Create#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/Form1.vb#3)]  
  
     これで、新しいアプリケーション設定を正常に作成し、指定されたプロパティにバインドしました。  
  
## <a name="net-framework-security"></a>.NET Framework セキュリティ  
 既定の設定プロバイダーの <xref:System.Configuration.LocalFileSettingsProvider> は、情報をプレーン テキストとして構成ファイルに保存します。 これにより、セキュリティがオペレーティング システムが現在のユーザーに対して提供するファイル アクセスのセキュリティに制限されます。 このため、構成ファイルに保存される情報に注意する必要があります。 たとえば、アプリケーション設定の一般的な用途の 1 つとして、アプリケーションのデータ ストアをポイントする接続文字列を格納します。 ただし、セキュリティの問題があるため、このような文字列にパスワードは含まれません。 接続文字列の詳細については、「<xref:System.Configuration.SpecialSetting>」を参照してください。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Configuration.SpecialSettingAttribute>
- <xref:System.Configuration.LocalFileSettingsProvider>
- [アプリケーション設定の概要](application-settings-overview.md)
- [方法: アプリケーション設定を検証します。](how-to-validate-application-settings.md)
