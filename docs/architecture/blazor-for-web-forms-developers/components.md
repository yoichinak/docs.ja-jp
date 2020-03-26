---
title: Blazor を使用して再利用可能な UI コンポーネントを構築する
description: Blazor を使用して再利用可能な UI コンポーネントを構築する方法と、それらのコンポーネントと Web フォーム コントロールの比較ASP.NETについて説明します。
author: danroth27
ms.author: daroth
ms.date: 09/18/2019
ms.openlocfilehash: 228f7aec4c7b87cb6d4127b55745f7a5ed90aaf9
ms.sourcegitcommit: b75a45f0cfe012b71b45dd9bf723adf32369d40c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/24/2020
ms.locfileid: "80228622"
---
# <a name="build-reusable-ui-components-with-blazor"></a>Blazor を使用して再利用可能な UI コンポーネントを構築する

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

web フォームASP.NET美しいことの 1 つは、再利用可能な UI コントロールに再利用可能なユーザー インターフェイス (UI) コードをカプセル化する方法です。 カスタム ユーザー コントロールは *、マークアップで定義できます.* また、デザイナーの完全なサポートを使用して、コード内に精巧なサーバー コントロールを構築することもできます。

Blazor は *、コンポーネント*を介した UI カプセル化もサポートしています。 コンポーネント:

- UI の自己完結型のチャンクです。
- 独自の状態とレンダリング ロジックを維持します。
- UI イベント ハンドラーの定義、入力データへのバインド、および独自のライフサイクルの管理を行うことができます。
- 通常は、Razor 構文を使用して *.razor*ファイルで定義されます。

## <a name="an-introduction-to-razor"></a>カミソリの紹介

Razor は、HTML と C# に基づく軽量マークアップテンプレート言語です。 Razor を使用すると、マークアップと C# コードの間でシームレスに遷移して、コンポーネントのレンダリング ロジックを定義できます。 razor*ファイル*がコンパイルされると、レンダリング ロジックは構造化された方法で .NET クラスにキャプチャされます。 コンパイルされたクラスの名前は *、.razor*ファイル名から取得されます。 名前空間は、プロジェクトの既定の名前空間とフォルダー パスから取得されるか、ディレクティブを使用して名前空間を`@namespace`明示的に指定できます (後述の Razor ディレクティブの詳細)。

コンポーネントのレンダリング ロジックは、C# を使用して追加された動的ロジックを使用して、通常の HTML マークアップを使用して作成されます。 文字`@`は C# に遷移するために使用されます。 Razor は、通常、HTML に切り替えたときに見つけ出す方法に関してスマートです。 たとえば、次のコンポーネントは現在の時間`<p>`を持つタグをレンダリングします。

```razor
<p>@DateTime.Now</p>
```

C# 式の先頭と末尾を明示的に指定するには、かっこを使用します。

```razor
<p>@(DateTime.Now)</p>
```

Razor では、レンダリング ロジックで C# の制御フローを簡単に使用できます。 たとえば、条件付きで次のような HTML をレンダリングできます。

```razor
@if (value % 2 == 0)
{
    <p>The value was even.</p>
}
```

または、次のように通常の C#`foreach`ループを使用して項目のリストを生成することもできます。

```razor
<ul>
@foreach (var item in items)
{
    <li>@item.Text</li>
}
</ul>
```

Razor ディレクティブは、ASP.NET Web フォームのディレクティブと同様に、Razor コンポーネントのコンパイル方法の多くの側面を制御します。 たとえば、コンポーネントの例を次に示します。

- 名前空間
- 基底クラス
- 実装されたインターフェイス
- ジェネリック パラメーター
- [インポートされた名前空間]
- ルート

Razor ディレクティブは`@`、文字で始まり、通常はファイルの先頭で新しい行の先頭で使用されます。 たとえば、ディレクティブは`@namespace`コンポーネントの名前空間を定義します。

```razor
@namespace MyComponentNamespace
```

次の表は、Blazor で使用される各種の Razor ディレクティブと、そのASP.NET Web フォームに相当するディレクティブ (存在する場合) を要約しています。

|ディレクティブ    |説明|例|Web フォームに相当するもの|
|-------------|-----------|-------|--------------------|
|`@attribute` |コンポーネントにクラス レベルの属性を追加します。|`@attribute [Authorize]`|なし|
|`@code`      |クラス メンバーをコンポーネントに追加します。|`@code { ... }`|`<script runat="server">...</script>`|
|`@implements`|指定されたインターフェイスを実装します。|`@implements IDisposable`|コードビハインドを使用する|
|`@inherits`  |指定した基本クラスを継承します。|`@inherits MyComponentBase`|`<%@ Control Inherits="MyUserControlBase" %>`|
|`@inject`    |コンポーネントにサービスを挿入します。|`@inject IJSRuntime JS`|なし|
|`@layout`    |コンポーネントのレイアウト コンポーネントを指定します。|`@layout MainLayout`|`<%@ Page MasterPageFile="~/Site.Master" %>`|
|`@namespace` |コンポーネントの名前空間を設定します。|`@namespace MyNamespace`|なし|
|`@page`      |コンポーネントのルートを指定します。|`@page "/product/{id}"`|`<%@ Page %>`|
|`@typeparam` |コンポーネントのジェネリック型パラメーターを指定します。|`@typeparam TItem`|コードビハインドを使用する|
|`@using`     |スコープに取り込む名前空間を指定します。|`@using MyComponentNamespace`|*web.config*に名前空間を追加する|

Razor コンポーネントは、要素に対する*ディレクティブ属性*を広範囲に使用して、コンポーネントのコンパイル方法 (イベント処理、データ バインディング、コンポーネント&要素参照など) のさまざまな側面を制御します。 ディレクティブ属性はすべて、括弧内の値がオプションである一般的なジェネリック構文に従います。

```razor
@directive(-suffix(:name))(="value")
```

次の表は、Blazor で使用される Razor ディレクティブのさまざまな属性をまとめたものです。

|属性    |説明|例|
|-------------|-----------|-------|
|`@attributes`|属性のディクショナリをレンダリングします。|`<input @attributes="ExtraAttributes" />`|
|`@bind`      |双方向のデータ バインディングを作成します。    |`<input @bind="username" @bind:event="oninput" />`|
|`@on{event}` |指定したイベントのイベント ハンドラーを追加します。|`<button @onclick="IncrementCount">Click me!</button>`|
|`@key`       |コレクション内の要素を保持するために、拡散アルゴリズムで使用するキーを指定します。|`<DetailsEditor @key="person" Details="person.Details" />`|
|`@ref`       |コンポーネントまたは HTML 要素への参照をキャプチャします。|`<MyDialog @ref="myDialog" />`|

Blazor (`@onclick`、 、、、`@bind``@ref`など) で使用されるさまざまなディレクティブ属性については、以下の章と後の章で説明します。

*.aspx*ファイルと *.ascx*ファイルで使用される構文の多くは、Razor で並列構文を持っています。 以下は、web フォームとカミソリのASP.NETの構文の簡単な比較です。

|機能                      |Web フォーム           |構文               |Razor         |構文 |
|-----------------------------|--------------------|---------------------|--------------|-------|
|ディレクティブ                   |`<%@ [directive] %>`|`<%@ Page %>`        |`@[directive]`|`@page`|
|コード ブロック                  |`<% %>`             |`<% int x = 123; %>` |`@{ }`        |`@{ int x = 123; }`|
|式<br>(HTML エンコード)|`<%: %>`            |`<%:DateTime.Now %>` |暗黙：`@`<br>明示的：`@()`|`@DateTime.Now`<br>`@(DateTime.Now)`|
|説明                     |`<%-- --%>`         |`<%-- Commented --%>`|`@* *@`       |`@* Commented *@`|
|データ バインディング                 |`<%# %>`            |`<%# Bind("Name") %>`|`@bind`       |`<input @bind="username" />`|

Razor コンポーネント クラスにメンバーを追加するには、`@code`ディレクティブを使用します。 この方法は、web フォーム`<script runat="server">...</script>`のユーザー コントロールまたはページASP.NETブロックを使用する方法と似ています。

```razor
@code {
    int count = 0;

    void IncrementCount()
    {
        count++;
    }
}
```

Razor は C# に基づいているため、C# プロジェクト (*.csproj*) 内からコンパイルする必要があります。 .razor ファイルは *.razor*、Visual Basic プロジェクト (*.vbproj*) からコンパイルできません。 ブラザプロジェクトから Visual Basic プロジェクトを参照することはできます。 その逆も当てはまります。

完全な Razor 構文のリファレンスについては、「 [ASP.NET コアの Razor 構文のリファレンス](/aspnet/core/mvc/views/razor)」を参照してください。

## <a name="use-components"></a>コンポーネントを使う

通常の HTML 以外にも、コンポーネントはレンダリング ロジックの一部として他のコンポーネントを使用できます。 Razor でコンポーネントを使用するための構文は、ASP.NET Web フォーム アプリでユーザー コントロールを使用するのと似ています。 コンポーネントは、コンポーネントの型名と一致する要素タグを使用して指定します。 たとえば、次のようなコンポーネントを`Counter`追加できます。

```razor
<Counter />
```

ASP.NET Web フォームとは異なり、Blazor のコンポーネント:

- 要素のプレフィックス (たとえば)`asp:`を使用しないでください。
- ページまたは*web.config*での登録は不要です。

.NET 型と同じように Razor コンポーネントを考えてみましょう。 コンポーネントを含むアセンブリが参照されている場合、そのコンポーネントは使用可能です。 コンポーネントの名前空間をスコープにするには、ディレクティブを適用します`@using`。

```razor
@using MyComponentLib

<Counter />
```

既定の Blazor プロジェクトで見られるように、ディレクティブを`@using`*_Imports.razor*ファイルに配置して、同じディレクトリ内および子ディレクトリ内のすべての *.razor*ファイルにインポートされるようにするのが一般的です。

コンポーネントの名前空間がスコープ内にない場合は、C# のように、完全な型名を使用してコンポーネントを指定できます。

```razor
<MyComponentLib.Counter />
```

## <a name="component-parameters"></a>コンポーネントのパラメーター

web フォームASP.NETでは、パブリック プロパティを使用して、パラメーターとデータをコントロールにフローできます。 これらのプロパティは、属性を使用してマークアップで設定することも、コードで直接設定することもできます。 Blazor コンポーネントは同様の方法で動作しますが、コンポーネントのプロパティにもコンポーネントパラメータ`[Parameter]`と見なされる属性を付ける必要があります。

次`Counter`のコンポーネントは、ボタンがクリック`IncrementAmount`されるたびにインクリメントする必要がある量を`Counter`指定するために使用できるコンポーネント パラメータを定義します。

```razor
<h1>Counter</h1>

<p>Current count: @currentCount</p>

<button class="btn btn-primary" @onclick="IncrementCount">Click me</button>

@code {
    int currentCount = 0;

    [Parameter]
    public int IncrementAmount { get; set; } = 1;

    void IncrementCount()
    {
        currentCount+=IncrementAmount;
    }
}
```

Blazor でコンポーネントパラメータを指定するには、Web フォームで使用するASP.NETと同じ属性を使用します。

```razor
<Counter IncrementAmount="10" />
```

## <a name="event-handlers"></a>イベント ハンドラー

web フォームと Blazor ASP.NETは、UI イベントを処理するためのイベント ベースのプログラミング モデルを提供します。 このようなイベントの例としては、ボタンのクリックやテキスト入力などがあります。 ASP.NET Web フォームでは、HTML サーバー コントロールを使用して DOM によって公開される UI イベントを処理したり、Web サーバー コントロールによって公開されるイベントを処理したりできます。 イベントは、フォームのポストバック要求を通じてサーバー上に表示されます。 次の Web フォーム ボタンのクリック例を考えてみましょう。

*カウンター.ascx*

```aspx-csharp
<asp:Button ID="ClickMeButton" runat="server" Text="Click me!" OnClick="ClickMeButton_Click" />
```

*Counter.ascx.cs*

```csharp
public partial class Counter : System.Web.UI.UserControl
{
    protected void ClickMeButton_Click(object sender, EventArgs e)
    {
        Console.WriteLine("The button was clicked!");
    }
}
```

Blazor では、FORM`@on{event}`のディレクティブ属性を使用して DOM UI イベントのハンドラを直接登録できます。 プレースホルダ`{event}`は、イベントの名前を表します。 たとえば、次のようなボタンのクリックをリッスンできます。

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    void OnClick()
    {
        Console.WriteLine("The button was clicked!);
    }
}
```

イベント ハンドラーは、イベントに関する詳細情報を提供するために、オプションのイベント固有の引数を受け入れることができます。 たとえば、マウス イベントは引数を`MouseEventArgs`取ることができますが、必須ではありません。

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    void OnClick(MouseEventArgs e)
    {
        Console.WriteLine($"Mouse clicked at {e.ScreenX}, {e.ScreenY}.");
    }
}
```

イベント ハンドラーのメソッド グループを参照する代わりに、ラムダ式を使用できます。 ラムダ式を使用すると、スコープ内の他の値を閉じることができます。

```razor
@foreach (var buttonLabel in buttonLabels)
{
    <button @onclick="() => Console.WriteLine($"The {buttonLabel} button was clicked!")">@buttonLabel</button>
}
```

イベント ハンドラは、同期的または非同期的に実行できます。 たとえば、次`OnClick`のイベント ハンドラーは非同期で実行されます。

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    async Task OnClick()
    {
        var result = await Http.GetAsync("api/values");
    }
}
```

イベントが処理されると、コンポーネントの状態が変更された場合に対応するようにコンポーネントがレンダリングされます。 非同期イベント ハンドラーを使用すると、コンポーネントはハンドラーの実行が完了した直後にレンダリングされます。 コンポーネントは、非同期`Task`の完了後に*再び*レンダリングされます。 この非同期実行モードは、非同期`Task`がまだ進行中の状態で、適切な UI を表示する機会を提供します。

```razor
<button @onclick="ShowMessage">Get message</button>

@if (showMessage)
{
    @if (message == null)
    {
        <p><em>Loading...</em></p>
    }
    else
    {
        <p>The message is: @message</p>
    }
}

@code
{
    bool showMessage = false;
    string message;

    public async Task ShowMessage()
    {
        showMessage = true;
        message = await MessageService.GetMessageAsync();
    }
}
```

コンポーネントは、 type`EventCallback<TValue>`のコンポーネント パラメータを定義することによって、独自のイベントを定義することもできます。 イベント コールバックは、オプションの引数、同期または非同期、メソッド グループ、ラムダ式など、DOM UI イベント ハンドラーのすべてのバリエーションをサポートします。

```razor
<button class="btn btn-primary" @onclick="OnClick">Click me!</button>

@code {
    [Parameter]
    public EventCallback<MouseEventArgs> OnClick { get; set; }
}
```

## <a name="data-binding"></a>データ バインディング

Blazor は、UI コンポーネントからコンポーネントの状態にデータをバインドする簡単なメカニズムを提供します。 この方法は、データ ソースから UI コントロールにデータをバインドする場合の、ASP.NET Web フォームの機能とは異なります。 「データの取り扱い」セクションで、さまざまなデータ ソースからの[データの処理について](data.md)説明します。

UI コンポーネントからコンポーネントの状態への双方向データ バインディングを作成するには、ディレクティブ属性を使用します`@bind`。 次の例では、チェック ボックスの値がフィールドに`isChecked`バインドされています。

```razor
<input type="checkbox" @bind="isChecked" />

@code {
    bool isChecked;
}
```

コンポーネントがレンダリングされると、チェックボックスの値はフィールドの値に設定されます`isChecked`。 ユーザーがチェックボックスを切り替えた場合`onchange`、イベントが発生し`isChecked`、フィールドが新しい値に設定されます。 この`@bind`場合の構文は、次のマークアップと同じです。

```razor
<input value="@isChecked" @onchange="(UIChangeEventArgs e) => isChecked = e.Value" />
```

バインドに使用するイベントを変更するには、 属性`@bind:event`を使用します。

```razor
<input @bind="text" @bind:event="oninput" />
<p>@text</p>

@code {
    string text;
}
```

コンポーネントは、パラメーターへのデータ バインディングもサポートできます。 データ バインドするには、バインド可能なパラメーターと同じ名前のイベント コールバック パラメーターを定義します。 名前に"変更済み" サフィックスが追加されます。

*パスワードボックス.カミソリ*

```razor
Password: <input
    value="@Password"
    @oninput="OnPasswordChanged"
    type="@(showPassword ? "text" : "password")" />

<label><input type="checkbox" @bind="showPassword" />Show password</label>

@code {
    private bool showPassword;

    [Parameter]
    public string Password { get; set; }

    [Parameter]
    public EventCallback<string> PasswordChanged { get; set; }

    private Task OnPasswordChanged(ChangeEventArgs e)
    {
        Password = e.Value.ToString();
        return PasswordChanged.InvokeAsync(Password);
    }
}
```

基になる UI 要素にデータ バインディングを連結するには、値を設定し、属性を使用する代わりに UI`@bind`要素で直接イベントを処理します。

コンポーネント・パラメーターにバインドするには、属性を`@bind-{Parameter}`使用して、バインドするパラメーターを指定します。

```razor
<PasswordBox @bind-Password="password" />

@code {
    string password;
}
```

## <a name="state-changes"></a>状態の変化

コンポーネントの状態が通常の UI イベントまたはイベント コールバックの外部で変更された場合、コンポーネントは再描画が必要であることを手動で通知する必要があります。 コンポーネントの状態が変化したことを通知するには、コンポーネントの`StateHasChanged`メソッドを呼び出します。

次の例では、コンポーネントは、アプリの`AppState`他の部分で更新できるサービスからのメッセージを表示します。 コンポーネントは`StateHasChanged`、メッセージが更新されるたびにコンポーネント`AppState.OnChange`がレンダリングされるように、そのメソッドをイベントに登録します。

```csharp
public class AppState
{
    public string Message { get; }

    // Lets components receive change notifications
    public event Action OnChange;

    public void UpdateMessage(string message)
    {
        shortlist.Add(itinerary);
        NotifyStateChanged();
    }

    private void NotifyStateChanged() => OnChange?.Invoke();
}
```

```razor
@inject AppState AppState

<p>App message: @AppState.Message</p>

@code {
    protected override void OnInitialized()
    {
        AppState.OnChange += StateHasChanged
    }
}
```

## <a name="component-lifecycle"></a>コンポーネントのライフサイクル

web フォーム フレームワークASP.NETには、モジュール、ページ、およびコントロールのライフサイクル メソッドが明確に定義されています。 たとえば、次のコントロールは、 、`Init``Load`およびライフサイクル イベントのイベント`UnLoad`ハンドラーを実装します。

*Counter.ascx.cs*

```csharp
public partial class Counter : System.Web.UI.UserControl
{
    protected void Page_Init(object sender, EventArgs e) { ... }
    protected void Page_Load(object sender, EventArgs e) { ... }
    protected void Page_UnLoad(object sender, EventArgs e) { ... }
}
```

Blazor コンポーネントには、明確に定義されたライフサイクルもあります。 コンポーネントのライフサイクルを使用して、コンポーネントの状態を初期化し、コンポーネントの高度な動作を実装できます。

Blazor のコンポーネントライフサイクルメソッドはすべて、同期バージョンと非同期バージョンの両方を備えています。 コンポーネントのレンダリングは同期的です。 コンポーネントのレンダリングの一部として非同期ロジックを実行することはできません。 すべての非同期ロジックは、ライフサイクル メソッドの`async`一部として実行する必要があります。

### <a name="oninitialized"></a>初期化中

`OnInitialized`メソッドと`OnInitializedAsync`メソッドは、コンポーネントの初期化に使用されます。 コンポーネントは通常、最初にレンダリングされた後に初期化されます。 コンポーネントが初期化された後、最終的に破棄される前に複数回レンダリングされることがあります。 この`OnInitialized`メソッドは、Web`Page_Load`フォーム ページおよびコントロールASP.NETでのイベントに似ています。

```csharp
protected override void OnInitialized() { ... }
protected override async Task OnInitializedAsync() { await ... }
```

### <a name="onparametersset"></a>パラメーターセット

`OnParametersSet`コンポーネントが`OnParametersSetAsync`親からパラメータを受け取り、値がプロパティに割り当てられると、 と メソッドが呼び出されます。 これらのメソッドは、コンポーネントの初期化後、および*コンポーネントがレンダリングされるたびに実行されます*。

```csharp
protected override void OnParametersSet() { ... }
protected override async Task OnParametersSetAsync() { await ... }
```

### <a name="onafterrender"></a>アフターレンダー

`OnAfterRender`と`OnAfterRenderAsync`メソッドは、コンポーネントのレンダリングが終了した後に呼び出されます。 要素参照とコンポーネント参照は、この時点で設定されます (詳細は、以下の概念)。 この時点で、ブラウザとの対話機能が有効になります。 DOM および JavaScript の実行との対話は安全に行うことができます。

```csharp
protected override void OnAfterRender(bool firstRender)
{
    if (firstRender)
    {
        ...
    }
}
protected override async Task OnAfterRenderAsync(bool firstRender)
{
    if (firstRender)
    {
        await ...
    }
}
```

`OnAfterRender``OnAfterRenderAsync`*サーバーでのプレレンダリング時に呼び出されません*。

この`firstRender`パラメーターは`true`、コンポーネントが最初にレンダリングされる時間です。それ以外の場合、`false`その値は です。

### <a name="idisposable"></a>IDisposable

Blazor コンポーネントは`IDisposable`、コンポーネントが UI から削除されたときにリソースを破棄するために実装できます。 Razor コンポーネントは、`IDispose`ディレクティブを`@implements`使用して実装できます。

```razor
@using System
@implements IDisposable

...

@code {
    public void Dispose()
    {
        ...
    }
}
```

## <a name="capture-component-references"></a>コンポーネント参照のキャプチャ

ASP.NET Web フォームでは、コントロールの ID を参照して、コード内でコントロール インスタンスを直接操作するのが一般的です。 Blazor では、コンポーネントへの参照をキャプチャして操作することも可能ですが、あまり一般的ではありません。

Blazor でコンポーネント参照をキャプチャするには、ディレクティブ`@ref`属性を使用します。 属性の値は、参照されるコンポーネントと同じ型の設定可能なフィールドの名前と一致する必要があります。

```razor
<MyLoginDialog @ref="loginDialog" ... />

@code {
    MyLoginDialog loginDialog;

    void OnSomething()
    {
        loginDialog.Show();
    }
}
```

親コンポーネントがレンダリングされると、フィールドに子コンポーネントインスタンスが設定されます。 その後、コンポーネント インスタンスに対してメソッドを呼び出したり、操作したりできます。

コンポーネント参照を使用してコンポーネントの状態を直接操作することはお勧めしません。 これにより、コンポーネントが正しい時刻に自動的にレンダリングされなくなります。

## <a name="capture-element-references"></a>要素参照のキャプチャ

Blazor コンポーネントは、要素への参照をキャプチャできます。 web フォーム ASP.NETの HTML サーバー コントロールとは異なり、Blazor の要素参照を使用して DOM を直接操作することはできません。 Blazor は DOM ディファリング アルゴリズムを使用して、ほとんどの DOM インタラクションを処理します。 Blazor でキャプチャされた要素参照は不透明です。 ただし、JavaScript 相互運用呼び出しで特定の要素参照を渡すために使用されます。 JavaScript 相互運用機能の詳細については、「[コア Blazor JavaScript の相互運用機能ASP.NET」](/aspnet/core/blazor/javascript-interop)を参照してください。

## <a name="templated-components"></a>テンプレート コンポーネント

ASP.NET Web フォームでは、 テンプレート*コントロール*を作成できます。 テンプレート コントロールを使用すると、開発者はコンテナ コントロールのレンダリングに使用する HTML の一部を指定できます。 テンプレート化されたサーバー コントロールを構築するしくみは複雑ですが、ユーザーがカスタマイズ可能な方法でデータをレンダリングする強力なシナリオを実現します。 テンプレート コントロールの例として`Repeater`は`DataList`、 および が含まれます。

Blazor コンポーネントは、型`RenderFragment`または`RenderFragment<T>`のコンポーネント パラメータを定義することによってテンプレート化することもできます。 A`RenderFragment`は、コンポーネントによってレンダリングできる Razor マークアップのチャンクを表します。 A`RenderFragment<T>`は、レンダリング フラグメントがレンダリングされるときに指定できるパラメーターを受け取る Razor マークアップのチャンクです。

### <a name="child-content"></a>子コンテンツ

Blazor コンポーネントは、子コンテンツを`RenderFragment`a としてキャプチャし、そのコンテンツをコンポーネントレンダリングの一部としてレンダリングできます。 子コンテンツをキャプチャするには、型`RenderFragment`のコンポーネント パラメータを定義し`ChildContent`、 という名前を付けます。

*かみそり*

```razor
<h1>Component with child content</h1>

<div>@ChildContent</div>

@code {
    [Parameter]
    public RenderFragment ChildContent { get; set; }
}
```

親コンポーネントは、通常の Razor 構文を使用して子コンテンツを指定できます。

```razor
<ChildContentComponent>
    <p>The time is @DateTime.Now</p>
</ChildContentComponent>
```

### <a name="template-parameters"></a>Template parameters

テンプレート化された Blazor コンポーネントは、型`RenderFragment`または`RenderFragment<T>`の複数のコンポーネントパラメータを定義することもできます。 のパラメーターは、`RenderFragment<T>`呼び出されたときに指定できます。 コンポーネントのジェネリック型パラメーターを指定するには、Razor ディレクティブ`@typeparam`を使用します。

*カミソリ*

```razor
@typeparam TItem

@Heading

<ul>
@foreach (var item in Items)
{
    <li>@ItemTemplate(item)</li>
}
</ul>

@code {
    [Parameter]
    public RenderFragment Heading { get; set; }

    [Parameter]
    public RenderFragment<TItem> ItemTemplate { get; set; }

    [Parameter]
    public IEnumerable<TItem> Items { get; set; }
}
```

テンプレート コンポーネントを使用する場合、テンプレート パラメーターは、パラメーターの名前に一致する子要素を使用して指定できます。 要素として渡される`RenderFragment<T>`型のコンポーネント引数には、 という`context`名前の暗黙のパラメータがあります。 この実装パラメーターの名前は、子要素の属性`Context`を使用して変更できます。 型パラメーターの名前と一致する属性を使用して、任意のジェネリック型パラメーターを指定できます。 可能であれば、型パラメーターは推論されます。

```razor
<SimpleListView Items="messages" TItem="string">
    <Heading>
        <h1>My list</h1>
    </Heading>
    <ItemTemplate Content="message">
        <p>The message is: @message</p>
    </ItemTemplate>
</SimpleListView>
```

このコンポーネントの出力は次のようになります。

```html
<h1>My list</h1>
<ul>
    <li>The message is: message1</li>
    <li>The message is: message2</li>
<ul>
```

## <a name="code-behind"></a>コードビハインド

通常、Blazor コンポーネントは、1 つの *.razor*ファイルで作成されます。 ただし、分離コード ファイルを使用してコードとマークアップを分離することもできます。 コンポーネント ファイルを使用するには、コンポーネント ファイルのファイル名と一致する C# ファイルを *.cs*追加します*Counter.razor.cs。* C# ファイルを使用して、コンポーネントの基本クラスを定義します。 基本クラスには、必要な名前を付けることができますが、クラスの名前はコンポーネント クラスと同じですが、`Base`拡張子が追加されています (`CounterBase`)。 コンポーネント ベースのクラスも`ComponentBase`から派生する必要があります。 次に、Razor コンポーネント ファイルで、`@inherits`コンポーネントの基本クラスを指定するディレクティブを追加`@inherits CounterBase`します ( ) 。

*カウンターカミソリ*

```razor
@inherits CounterBase

<h1>Counter</h1>

<p>Current count: @currentCount</p>

<button @onclick="IncrementCount">Click me</button>
```

*Counter.razor.cs*

```csharp
public class CounterBase : ComponentBase
{
    protected int currentCount = 0;

    protected void IncrementCount()
    {
        currentCount++;
    }
}
```

基本クラス内のコンポーネントのメンバーの可視性は、コンポーネント クラス`protected`に`public`対して可視であるか、またはコンポーネント クラスから参照可能である必要があります。

## <a name="additional-resources"></a>その他のリソース

上記は、Blazor コンポーネントのすべての側面を網羅的に扱うものではありません。 [作成し、コア Razor コンポーネントを使用する](/aspnet/core/blazor/components)方法の詳細については、ASP.NETのドキュメントを参照してください。

>[!div class="step-by-step"]
>[前次](app-startup.md)
>[Next](pages-routing-layouts.md)
