---
title: '方法: アプリケーション設定を検証する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- validating application settings
- application settings [Windows Forms], Windows Forms
- application settings [Windows Forms], validating
ms.assetid: 9f145ada-4267-436a-aa4c-c4dcffd0afb7
ms.openlocfilehash: b7aba4935756fc218a1fadaa1dd9f20a5bc3034f
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59317891"
---
# <a name="how-to-validate-application-settings"></a>方法: アプリケーション設定を検証する
このトピックでは、アプリケーション設定を永続化する前に検証する方法について説明します。  
  
 アプリケーション設定は厳密に型指定されているため、ユーザーが特定の設定に誤った型のデータを割り当てることはほとんどありません。 しかし、誕生日として未来の日付を入力するなど、ユーザーが許容範囲外の値を設定に割り当てようとする場合もあります。 <xref:System.Configuration.ApplicationSettingsBase>を、すべてのアプリケーション設定クラスの親クラスは、このような境界のチェックを有効にする 4 つのイベントを公開します。 これらのイベントを処理すると、検証コードがプロジェクト全体に分散するのではなく、すべての検証コードが 1 か所に配置されます。  
  
 次の表に示すように、使用するイベントは設定をいつ検証する必要があるかによって決まります。  
  
|event|発生と使用|  
|-----------|------------------------|  
|<xref:System.Configuration.ApplicationSettingsBase.SettingsLoaded>|設定プロパティ グループの初期読み込み後に発生します。<br /><br /> プロパティ グループ全体の初期値がアプリケーション内で使用される前に値を検証するには、このイベントを使用します。|  
|<xref:System.Configuration.ApplicationSettingsBase.SettingChanging>|1 つの設定プロパティの値が変更される前に発生します。<br /><br /> 1 つのプロパティが変更される前にプロパティを検証するには、このイベントを使用します。 アクションと選択に関するフィードバックをユーザーにすぐに提供できます。|  
|<xref:System.Configuration.ApplicationSettingsBase.PropertyChanged>|1 つの設定プロパティの値が変更された後に発生します。<br /><br /> 1 つのプロパティが変更された後にプロパティを検証するには、このイベントを使用します。 時間がかかる非同期の検証プロセスが必要な場合を除き、このイベントを検証に使用することはほとんどありません。|  
|<xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>|設定プロパティ グループが保存される前に発生します。<br /><br /> プロパティ グループ全体の値がディスクに永続化される前に値を検証するには、このイベントを使用します。|  
  
 通常は、検証のために同じアプリケーション内でこれらのイベントをすべて使用するわけではありません。 たとえば、ことのみを処理することによってすべての検証要件を満たすためには多くの場合、<xref:System.Configuration.ApplicationSettingsBase.SettingChanging>イベント。  
  
 イベント ハンドラーは、無効な値を検出すると、一般に次のいずれかのアクションを実行します。  
  
-   既定値など、正しいことがわかっている値を自動的に入力します。  
  
-   サーバー コードのユーザーに情報を再度照会します。  
  
-   などの関連付けられたアクションの前に発生したイベントの<xref:System.Configuration.ApplicationSettingsBase.SettingChanging>と<xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>を使用して、<xref:System.ComponentModel.CancelEventArgs>操作をキャンセルする引数。  
  
 イベント処理の詳細については、「[イベント ハンドラーの概要 (Windows フォーム)](../event-handlers-overview-windows-forms.md)」を参照してください。  
  
 次の手順は、いずれかを使用して有効な生年月日をテストする方法を示して、<xref:System.Configuration.ApplicationSettingsBase.SettingChanging>または<xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>イベント。 これらの手順は、アプリケーション設定を既に作成していることを前提としています。この例では、`DateOfBirth` という名前の設定の範囲チェックを実行します。 設定の作成の詳細については、次を参照してください。[方法。アプリケーション設定を作成する](how-to-create-application-settings.md)します。  
  
### <a name="to-obtain-the-application-settings-object"></a>アプリケーション設定オブジェクトを取得するには  
  
-   次の項目のいずれかを実行して、アプリケーション設定オブジェクト (ラッパー インスタンス) への参照を取得します。  
  
    -   Visual Studio の**プロパティ エディター**で [アプリケーション設定] ダイアログ ボックスを使用して設定を作成した場合は、次の式によって、使用している言語用に生成された既定の設定オブジェクトを取得できます。  
  
        ```csharp  
        Configuration.Settings.Default   
        ```  
  
        ```vb  
        MySettings.Default   
        ```  
  
         - または -  
  
    -   Visual Basic 開発者がプロジェクト デザイナーを使用してアプリケーション設定を作成した場合は、[My.Settings オブジェクト](~/docs/visual-basic/language-reference/objects/my-settings-object.md)を使用して設定を取得できます。  
  
         - または -  
  
    -   派生することによって、設定を作成した場合<xref:System.Configuration.ApplicationSettingsBase>を直接手動で、クラスのインスタンスを作成する必要があります。  
  
        ```csharp  
        MyCustomSettings settings = new MyCustomSettings();  
        ```  
  
        ```vb  
        Dim Settings as New MyCustomSettings()  
        ```  
  
 以下の手順は、この手順の最後の項目を実行してアプリケーション設定オブジェクトを取得したことを前提としています。  
  
### <a name="to-validate-application-settings-when-a-setting-is-changing"></a>設定の変更時にアプリケーション設定を検証するには  
  
1. 使用する場合、C#開発者は、フォームまたはコントロールの`Load`イベント、イベント ハンドラーを追加、<xref:System.Configuration.ApplicationSettingsBase.SettingChanging>イベント。  
  
     - または -  
  
     Visual Basic 開発者の場合、`WithEvents` キーワードを使用して `Settings` 変数を宣言します。  
  
    ```csharp  
    public void Form1_Load(Object sender, EventArgs e)   
    {  
        settings.SettingChanging += new SettingChangingEventHandler(MyCustomSettings_SettingChanging);  
    }  
    ```  
  
    ```vb  
    Public Sub Form1_Load(sender as Object, e as EventArgs)  
        AddHandler settings.SettingChanging, AddressOf MyCustomSettings_SettingChanging  
    End Sub   
    ```  
  
2. イベント ハンドラーを定義し、誕生日の範囲チェックを実行するコードをイベント ハンドラー内に記述します。  
  
    ```csharp  
    private void MyCustomSettings_SettingChanging(Object sender, SettingChangingEventArgs e)  
    {  
        if (e.SettingName.Equals("DateOfBirth")) {  
            Date newDate = (Date)e.NewValue;  
            If (newDate > Date.Now) {  
                e.Cancel = true;  
                // Inform the user.  
            }  
        }  
    }  
    ```  
  
    ```vb  
    Private Sub MyCustomSettings_SettingChanging(sender as Object, e as SettingChangingEventArgs) Handles Settings.SettingChanging  
        If (e.SettingName.Equals("DateOfBirth")) Then  
            Dim NewDate as Date = CType(e.NewValue, Date)  
            If (NewDate > Date.Now) Then  
                e.Cancel = True  
                ' Inform the user.  
            End If  
        End If  
    End Sub  
    ```  
  
### <a name="to-validate-application-settings-when-a-save-occurs"></a>保存時にアプリケーション設定を検証するには  
  
1. フォームまたはコントロールの`Load`イベントのイベント ハンドラーを追加、<xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>イベント。  
  
    ```csharp  
    public void Form1_Load(Object sender, EventArgs e)   
    {  
        settings.SettingsSaving += new SettingsSavingEventHandler(MyCustomSettings_SettingsSaving);  
    }  
    ```  
  
    ```vb  
    Public Sub Form1_Load(Sender as Object, e as EventArgs)  
        AddHandler settings.SettingsSaving, AddressOf MyCustomSettings_SettingsSaving  
    End Sub  
    ```  
  
2. イベント ハンドラーを定義し、誕生日の範囲チェックを実行するコードをイベント ハンドラー内に記述します。  
  
    ```csharp  
    private void MyCustomSettings_SettingsSaving(Object sender, SettingsSavingEventArgs e)  
    {  
        if (this["DateOfBirth"] > Date.Now) {  
            e.Cancel = true;  
        }  
    }  
    ```  
  
    ```vb  
    Private Sub MyCustomSettings_SettingsSaving(Sender as Object, e as SettingsSavingEventArgs)  
        If (Me["DateOfBirth"] > Date.Now) Then  
            e.Cancel = True  
        End If  
    End Sub  
    ```  
  
## <a name="see-also"></a>関連項目

- [Windows フォーム内でのイベント ハンドラーの作成](../creating-event-handlers-in-windows-forms.md)
- [方法: アプリケーション設定を作成する](how-to-create-application-settings.md)
