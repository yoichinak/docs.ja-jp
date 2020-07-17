---
title: カスタム コントロールのアプリケーション設定
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], application settings
- application settings [Windows Forms], custom controls
ms.assetid: f44afb74-76cc-44f2-890a-44b7cdc211a1
ms.openlocfilehash: a4e477ce1c171b514482623595b2c5565564a2cb
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040460"
---
# <a name="application-settings-for-custom-controls"></a>カスタム コントロールのアプリケーション設定
コントロールがサードパーティ製アプリケーションでホストされている場合は、カスタムコントロールにアプリケーション設定を保持する機能を提供するために、特定のタスクを完了する必要があります。

 アプリケーション設定機能に関するドキュメントのほとんどは、スタンドアロンアプリケーションを作成することを前提として記述されています。 ただし、他の開発者がアプリケーションでホストするコントロールを作成する場合は、コントロールが設定を適切に保持するために、追加の手順をいくつか実行する必要があります。

## <a name="application-settings-and-custom-controls"></a>アプリケーション設定とカスタムコントロール
 コントロールで設定を適切に永続化するには、から<xref:System.Configuration.ApplicationSettingsBase>派生した独自の専用アプリケーション設定ラッパークラスを作成することによって、プロセスをカプセル化する必要があります。 また、メインコントロールクラスはを実装<xref:System.Configuration.IPersistComponentSettings>する必要があります。 インターフェイスには、と<xref:System.Configuration.IPersistComponentSettings.LoadComponentSettings%2A> <xref:System.Configuration.IPersistComponentSettings.SaveComponentSettings%2A>という2つのメソッドと共に、いくつかのプロパティが含まれています。 Visual Studio の**Windows フォームデザイナー**を使用してコントロールをフォームに追加すると、コントロールが<xref:System.Configuration.IPersistComponentSettings.LoadComponentSettings%2A>初期化されるときに Windows フォームが自動的に呼び出さ<xref:System.Configuration.IPersistComponentSettings.SaveComponentSettings%2A>れます。 `Dispose`コントロールのメソッドでを呼び出す必要があります。

 さらに、カスタムコントロールのアプリケーション設定が Visual Studio などのデザイン時環境で適切に機能するためには、次のものを実装する必要があります。

1. を1つのパラメーター <xref:System.ComponentModel.IComponent>として受け取るコンストラクターを持つカスタムアプリケーション設定クラス。 このクラスを使用すると、すべてのアプリケーション設定を保存して読み込むことができます。 このクラスの新しいインスタンスを作成するときは、コンストラクターを使用してカスタムコントロールを渡します。

2. フォームの<xref:System.Windows.Forms.Form.Load>イベントハンドラーなど、コントロールを作成してフォームに配置した後に、このカスタム設定クラスを作成します。

 カスタム設定クラスを作成する方法について[は、「方法:アプリケーション設定](how-to-create-application-settings.md)を作成します。

## <a name="settings-keys-and-shared-settings"></a>設定キーと共有設定
 一部のコントロールは、同じフォーム内で複数回使用できます。 ほとんどの場合、これらのコントロールは個別の設定を保持する必要があります。 <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A> の<xref:System.Configuration.IPersistComponentSettings>プロパティを使用すると、フォーム上のコントロールの複数のバージョンを明確に区別するために機能する一意の文字列を指定できます。

 を実装<xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A>する最も簡単な方法は、 <xref:System.Windows.Forms.Control.Name%2A> <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A>のコントロールのプロパティを使用することです。 コントロールの設定を読み込んだ場合、または保存した場合<xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A>は、の<xref:System.Configuration.ApplicationSettingsBase.SettingsKey%2A>値を<xref:System.Configuration.ApplicationSettingsBase>クラスのプロパティに渡します。 アプリケーション設定は、ユーザーの設定を XML に永続化するときに、この一意のキーを使用します。 次のコード例は、 `<userSettings>` `Text`プロパティの設定を保存するという名前`CustomControl1`のカスタムコントロールのインスタンスをセクションが検索する方法を示しています。

```xml
<userSettings>
    <CustomControl1>
        <setting name="Text" serializedAs="string">
            <value>Hello, World</value>
        </setting>
    </CustomControl1>
</userSettings>
```

 の<xref:System.Configuration.ApplicationSettingsBase.SettingsKey%2A>値が指定されていないコントロールのインスタンスは、同じ設定を共有します。

## <a name="see-also"></a>関連項目

- <xref:System.Configuration.ApplicationSettingsBase>
- <xref:System.Configuration.IPersistComponentSettings>
- [アプリケーション設定アーキテクチャ](application-settings-architecture.md)
