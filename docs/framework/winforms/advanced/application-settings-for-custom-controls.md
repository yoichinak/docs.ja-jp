---
title: カスタム コントロールのアプリケーション設定
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], application settings
- application settings [Windows Forms], custom controls
ms.assetid: f44afb74-76cc-44f2-890a-44b7cdc211a1
ms.openlocfilehash: 69a5caef8bab45503b9f34422de8c2ba2e7f01ff
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59317299"
---
# <a name="application-settings-for-custom-controls"></a>カスタム コントロールのアプリケーション設定
コントロールがサード パーティ製のアプリケーションでホストされている場合は、アプリケーションの設定を保存する機能、カスタム コントロールを提供する特定のタスクを完了する必要があります。  
  
 アプリケーション設定機能についてのドキュメントのほとんどは、スタンドアロン アプリケーションを作成することを前提として書き込まれます。 ただし場合は、アプリケーションで他の開発者をホストするコントロールを作成する必要がありますの設定を保持するコントロールのいくつかの追加手順を実行する適切です。  
  
## <a name="application-settings-and-custom-controls"></a>アプリケーションの設定とカスタム コントロール  
 その設定を正しく保持する、コントロールの設定ラッパー クラスから派生した独自の専用アプリケーションを作成して、プロセスをカプセルにする必要があります<xref:System.Configuration.ApplicationSettingsBase>します。 また、メインのコントロール クラスを実装する必要があります、<xref:System.Configuration.IPersistComponentSettings>します。 インターフェイスには、2 つのメソッドに加えていくつかのプロパティが含まれます。<xref:System.Configuration.IPersistComponentSettings.LoadComponentSettings%2A>と<xref:System.Configuration.IPersistComponentSettings.SaveComponentSettings%2A>します。 使用してフォームにコントロールを追加する場合、 **Windows フォーム デザイナー** Windows フォームを呼び出し、Visual Studio で<xref:System.Configuration.IPersistComponentSettings.LoadComponentSettings%2A>コントロールが初期化される場合に自動的に呼び出す必要があります<xref:System.Configuration.IPersistComponentSettings.SaveComponentSettings%2A>で自分で、 `Dispose`コントロールのメソッド。  
  
 さらに、Visual Studio などのデザイン時環境で適切に機能するカスタム コントロールのアプリケーション設定の順序で、次を実装する必要があります。  
  
1. 受け取るコンス トラクターを持つカスタム アプリケーション設定クラスを<xref:System.ComponentModel.IComponent>パラメーターを 1 つ。 保存し、すべてのアプリケーションの設定を読み込むには、このクラスを使用します。 このクラスの新しいインスタンスを作成するときは、コンス トラクターを使用して、カスタム コントロールを渡します。  
  
2. コントロールを作成し、フォームのように、フォームに配置した後、このカスタム設定クラスを作成<xref:System.Windows.Forms.Form.Load>イベント ハンドラー。  
  
 カスタム設定クラスを作成する方法の詳細については、次を参照してください。[方法。アプリケーション設定を作成する](how-to-create-application-settings.md)します。  
  
## <a name="settings-keys-and-shared-settings"></a>設定キーと共有設定  
 一部のコントロールを同じフォーム内で複数回使用できます。 ほとんどの場合、これらのコントロールを各自の設定を保持します。 <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A>プロパティ<xref:System.Configuration.IPersistComponentSettings>フォーム上のコントロールの複数のバージョンを解消するために機能する一意の文字列を指定することができます。  
  
 実装する最も簡単な方法は、<xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A>を使用して、<xref:System.Windows.Forms.Control.Name%2A>のコントロールのプロパティ、<xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A>します。 値を渡すロードまたはコントロールの設定を保存するときに<xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A>に、<xref:System.Configuration.ApplicationSettingsBase.SettingsKey%2A>のプロパティ、<xref:System.Configuration.ApplicationSettingsBase>クラス。 アプリケーションの設定は、XML に、ユーザーの設定が引き続き発生するときに、この一意のキーを使用します。 次のコード例に示す方法、`<userSettings>`セクションという名前のカスタム コントロールのインスタンスを探すことがあります`CustomControl1`の設定を保存するその`Text`プロパティ。  
  
```xml  
<userSettings>  
    <CustomControl1>  
        <setting name="Text" serializedAs="string">  
            <value>Hello, World</value>  
        </setting>  
    </CustomControl1>  
</userSettings>  
```  
  
 すべてのインスタンスの値を指定されていないコントロールの<xref:System.Configuration.ApplicationSettingsBase.SettingsKey%2A>同じ設定で共有されます。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Configuration.ApplicationSettingsBase>
- <xref:System.Configuration.IPersistComponentSettings>
- [アプリケーション設定アーキテクチャ](application-settings-architecture.md)
