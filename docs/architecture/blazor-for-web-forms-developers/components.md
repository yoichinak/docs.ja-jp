---
title: Blazor を使用して再利用可能な UI コンポーネントを構築する
description: Blazor を使用して再利用可能な UI コンポーネントを構築する方法と、それらを ASP.NET Web フォームコントロールと比較する方法について説明します。
author: danroth27
ms.author: daroth
ms.date: 09/18/2019
ms.openlocfilehash: 79fb2338a981389c3750e884ce6606351c84738a
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/29/2020
ms.locfileid: "82506767"
---
# <a name="build-reusable-ui-components-with-blazor"></a>Blazor を使用して再利用可能な UI コンポーネントを構築する

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

ASP.NET Web フォームに関するすばらしい点の1つは、再利用可能なユーザーインターフェイス (UI) コードを再利用可能な UI コントロールにカプセル化できるようにする方法です。 カスタムユーザーコントロールは、 *.ascx*ファイルを使用してマークアップで定義できます。 デザイナーを完全にサポートするコードで、複雑なサーバーコントロールを作成することもできます。

Blazor は、*コンポーネント*による UI カプセル化もサポートしています。 コンポーネント:

- は、UI の自己完結型のチャンクです。
- は、独自の状態およびレンダリングロジックを保持します。
- UI イベントハンドラーを定義し、入力データにバインドして、独自のライフサイクルを管理できます。
- は、通常、Razor 構文を使用する*razor*ファイルで定義されます。

## <a name="an-introduction-to-razor"></a>Razor の概要

Razor は、HTML および C# に基づく軽量のマークアップテンプレート言語です。 Razor を使用すると、マークアップと C# のコードをシームレスに切り替えて、コンポーネントのレンダリングロジックを定義できます。 *Razor*ファイルがコンパイルされると、レンダリングロジックは .net クラスで構造化された方法でキャプチャされます。 コンパイル済みクラスの名前は、 *razor*ファイル名から取得されます。 名前空間は、プロジェクトの既定の名前空間およびフォルダーパスから取得されます。また、 `@namespace`ディレクティブを使用して名前空間を明示的に指定することもできます (以下の Razor ディレクティブについてはこちらを参照してください)。

コンポーネントのレンダリングロジックは、C# を使用して動的なロジックが追加された通常の HTML マークアップを使用して作成されます。 文字`@`は、C# に移行するために使用されます。 Razor は、通常、HTML に切り替えたときに理解することが賢明です。 たとえば、次のコンポーネントは、現在`<p>`の時刻を使用してタグをレンダリングします。

```razor
<p>@DateTime.Now</p>
```

C# 式の開始と終了を明示的に指定するには、かっこを使用します。

```razor
<p>@(DateTime.Now)</p>
```

Razor では、レンダリングロジックで C# の制御フローを簡単に使用することもできます。 たとえば、次のような HTML を条件付きでレンダリングできます。

```razor
@if (value % 2 == 0)
{
    <p>The value was even.</p>
}
```

または、次のような通常の C# `foreach`ループを使用して項目の一覧を生成することもできます。

```razor
<ul>
@foreach (var item in items)
{
    <li>@item.Text</li>
}
</ul>
```

Razor ディレクティブは、ASP.NET Web フォームのディレクティブと同様に、Razor コンポーネントのコンパイル方法の多くの側面を制御します。 コンポーネントの例を次に示します。

- 名前空間
- 基底クラス
- 実装されたインターフェイス
- ジェネリックパラメーター
- [インポートされた名前空間]
- ルート

Razor ディレクティブは、 `@`文字で始まり、通常、ファイルの先頭にある新しい行の先頭で使用されます。 たとえば、ディレクティブは`@namespace`コンポーネントの名前空間を定義します。

```razor
@namespace MyComponentNamespace
```

次の表は、Blazor で使用されるさまざまな Razor ディレクティブとそれらの ASP.NET Web フォームに相当するものをまとめたものです (存在する場合)。

|ディレクティブ    |説明|例|同等の Web フォーム|
|-------------|-----------|-------|--------------------|
|`@attribute` |コンポーネントにクラスレベルの属性を追加します。|`@attribute [Authorize]`|なし|
|`@code`      |コンポーネントにクラスメンバーを追加します。|`@code { ... }`|`<script runat="server">...</script>`|
|`@implements`|指定したインターフェイスを実装します。|`@implements IDisposable`|コードビハインドを使用する|
|`@inherits`  |指定した基底クラスから継承します。|`@inherits MyComponentBase`|`<%@ Control Inherits="MyUserControlBase" %>`|
|`@inject`    |コンポーネントにサービスを挿入します。|`@inject IJSRuntime JS`|なし|
|`@layout`    |コンポーネントのレイアウトコンポーネントを指定します。|`@layout MainLayout`|`<%@ Page MasterPageFile="~/Site.Master" %>`|
|`@namespace` |コンポーネントの名前空間を設定します。|`@namespace MyNamespace`|なし|
|`@page`      |コンポーネントのルートを指定します。|`@page "/product/{id}"`|`<%@ Page %>`|
|`@typeparam` |コンポーネントのジェネリック型パラメーターを指定します。|`@typeparam TItem`|コードビハインドを使用する|
|`@using`     |スコープに取り込む名前空間を指定します|`@using MyComponentNamespace`|*Web.config に名前*空間を追加する|

また、Razor コンポーネントでは、要素に対して*ディレクティブ属性*を広範に使用して、コンポーネントのコンパイル (イベント処理、データバインディング、コンポーネント & 要素参照など) のさまざまな側面を制御します。 ディレクティブ属性は、かっこ内の値が省略可能である一般的なジェネリック構文に従います。

```razor
@directive(-suffix(:name))(="value")
```

次の表は、Blazor で使用される Razor ディレクティブのさまざまな属性をまとめたものです。

|属性    |説明|例|
|-------------|-----------|-------|
|`@attributes`|属性のディクショナリをレンダリングします|`<input @attributes="ExtraAttributes" />`|
|`@bind`      |双方向のデータバインディングを作成します。    |`<input @bind="username" @bind:event="oninput" />`|
|`@on{event}` |指定したイベントのイベントハンドラーを追加します。|`<button @onclick="IncrementCount">Click me!</button>`|
|`@key`       |コレクション内の要素を保持するために比較アルゴリズムによって使用されるキーを指定します。|`<DetailsEditor @key="person" Details="person.Details" />`|
|`@ref`       |コンポーネントまたは HTML 要素への参照をキャプチャします。|`<MyDialog @ref="myDialog" />`|

Blazor によって使用されるさまざま`@onclick`な`@bind`ディレクティブ`@ref`属性 (、、など) については、以降の章で説明します。

*.Aspx*および *.ascx*ファイルで使用される構文の多くには、Razor の並列構文があります。 次に、ASP.NET Web フォームと Razor の構文を簡単に比較します。

|機能                      |Web フォーム           |構文               |Razor         |構文 |
|-----------------------------|--------------------|---------------------|--------------|-------|
|ディレクティブ                   |`<%@ [directive] %>`|`<%@ Page %>`        |`@[directive]`|`@page`|
|コード ブロック                  |`<% %>`             |`<% int x = 123; %>` |`@{ }`        |`@{ int x = 123; }`|
|式<br>(HTML エンコード)|`<%: %>`            |`<%:DateTime.Now %>` |順序`@`<br>順序`@()`|`@DateTime.Now`<br>`@(DateTime.Now)`|
|説明                     |`<%-- --%>`         |`<%-- Commented --%>`|`@* *@`       |`@* Commented *@`|
|データ バインディング                 |`<%# %>`            |`<%# Bind("Name") %>`|`@bind`       |`<input @bind="username" />`|

Razor コンポーネントクラスにメンバーを追加するには`@code` 、ディレクティブを使用します。 この手法は、ASP.NET Web フォーム`<script runat="server">...</script>`のユーザーコントロールまたはページでブロックを使用するのと似ています。

```razor
@code {
    int count = 0;

    void IncrementCount()
    {
        count++;
    }
}
```

Razor は c# に基づいているため、C# プロジェクト (*.csproj*) 内からコンパイルする必要があります。 Visual Basic プロジェクト (*.vbproj*) から*razor*ファイルをコンパイルすることはできません。 Blazor プロジェクトから Visual Basic プロジェクトを参照することもできます。 逆も同様です。

完全 Razor 構文リファレンスについては、「 [ASP.NET Core の Razor 構文リファレンス](/aspnet/core/mvc/views/razor)」を参照してください。

## <a name="use-components"></a>コンポーネントを使う

通常の HTML とは別に、コンポーネントはレンダリングロジックの一部として他のコンポーネントを使用することもできます。 Razor でコンポーネントを使用するための構文は、ASP.NET Web フォームアプリでユーザーコントロールを使用する場合と似ています。 コンポーネントは、コンポーネントの型名と一致する要素タグを使用して指定されます。 たとえば、次のようなコンポーネント`Counter`を追加できます。

```razor
<Counter />
```

ASP.NET Web フォームとは異なり、Blazor のコンポーネントは次のとおりです。

- 要素のプレフィックスは使用しないでください`asp:`(たとえば、)。
- ページまた*は web.config で*の登録は必要ありません。

.NET 型のような Razor コンポーネントについて考えてみましょう。これはまさにそのようなものです。 コンポーネントを含むアセンブリが参照されている場合は、コンポーネントを使用できます。 コンポーネントの名前空間をスコープに入れるには、 `@using`ディレクティブを適用します。

```razor
@using MyComponentLib

<Counter />
```

既定の Blazor プロジェクトに示されているように、ディレクティブ`@using`を _Imports の*razor*ファイルに配置するのが一般的です。これにより、同じディレクトリおよび子ディレクトリ内のすべての*razor*ファイルにディレクティブがインポートされます。

コンポーネントの名前空間がスコープ内にない場合は、C# の場合と同様に、完全な型名を使用してコンポーネントを指定できます。

```razor
<MyComponentLib.Counter />
```

## <a name="component-parameters"></a>コンポーネントのパラメーター

ASP.NET Web フォームでは、パブリックプロパティを使用して、パラメーターとデータをコントロールにフローできます。 これらのプロパティは、属性を使用してマークアップで設定することも、コードで直接設定することもできます。 Blazor コンポーネントは同様の方法で動作しますが、コンポーネントのプロパティは、コンポーネント`[Parameter]`のパラメーターと見なされるように属性でマークする必要もあります。

次`Counter`のコンポーネントでは、ボタンが`IncrementAmount`クリックされるたびにが`Counter`インクリメントされる量を指定するために使用できる、というコンポーネントパラメーターを定義しています。

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

Blazor でコンポーネントパラメーターを指定するには、ASP.NET Web フォームの場合と同様に属性を使用します。

```razor
<Counter IncrementAmount="10" />
```

## <a name="event-handlers"></a>イベント ハンドラー

ASP.NET Web Forms と Blazor はどちらも、UI イベントを処理するためのイベントベースのプログラミングモデルを提供します。 このようなイベントの例としては、ボタンのクリックやテキスト入力などがあります。 ASP.NET Web フォームでは、HTML サーバーコントロールを使用して、DOM によって公開される UI イベントを処理したり、web サーバーコントロールによって公開されるイベントを処理したりすることができます。 イベントは、ポストバック要求のフォームを使用してサーバー上に表示されます。 次の Web フォームのボタンをクリックする例を考えてみましょう。

*カウンタ .ascx*

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

Blazor では、フォーム`@on{event}`のディレクティブ属性を使用して、DOM UI イベントのハンドラーを直接登録できます。 プレースホルダー `{event}`は、イベントの名前を表します。 たとえば、次のようなボタンのクリックをリッスンできます。

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    void OnClick()
    {
        Console.WriteLine("The button was clicked!);
    }
}
```

イベントハンドラーは、イベントに関する詳細情報を提供するために、省略可能なイベント固有の引数を受け取ることができます。 たとえば、マウスイベントは`MouseEventArgs`引数を受け取ることができますが、必須ではありません。

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    void OnClick(MouseEventArgs e)
    {
        Console.WriteLine($"Mouse clicked at {e.ScreenX}, {e.ScreenY}.");
    }
}
```

イベントハンドラーのメソッドグループを参照する代わりに、ラムダ式を使用できます。 ラムダ式を使用すると、他のスコープ内の値を閉じることができます。

```razor
@foreach (var buttonLabel in buttonLabels)
{
    <button @onclick="() => Console.WriteLine($"The {buttonLabel} button was clicked!")">@buttonLabel</button>
}
```

イベントハンドラーは、同期または非同期で実行できます。 たとえば、次`OnClick`のイベントハンドラーは非同期的に実行されます。

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    async Task OnClick()
    {
        var result = await Http.GetAsync("api/values");
    }
}
```

イベントが処理されると、コンポーネントは、コンポーネントの状態の変更を考慮してレンダリングされます。 非同期イベントハンドラーを使用すると、ハンドラーの実行が完了した直後にコンポーネントがレンダリングされます。 非同期`Task`の完了後に、コンポーネントが*再び*表示されます。 この非同期実行モードでは、非同期`Task`の処理中に適切な UI を表示することができます。

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

コンポーネントは、型`EventCallback<TValue>`のコンポーネントパラメーターを定義することで、独自のイベントを定義することもできます。 イベントコールバックは、省略可能な引数、同期または非同期、メソッドグループ、ラムダ式など、DOM UI イベントハンドラーのすべてのバリエーションをサポートします。

```razor
<button class="btn btn-primary" @onclick="OnClick">Click me!</button>

@code {
    [Parameter]
    public EventCallback<MouseEventArgs> OnClick { get; set; }
}
```

## <a name="data-binding"></a>データ バインディング

Blazor には、UI コンポーネントからコンポーネントの状態にデータをバインドするための単純なメカニズムが用意されています。 この方法は、データソースから UI コントロールにデータをバインドするための ASP.NET Web フォームの機能とは異なります。 データの処理に[関する](data.md)セクションでは、さまざまなデータソースからのデータの処理について説明します。

UI コンポーネントからコンポーネントの状態への双方向のデータバインディングを作成するには、 `@bind`ディレクティブ属性を使用します。 次の例では、チェックボックスの値が`isChecked`フィールドにバインドされています。

```razor
<input type="checkbox" @bind="isChecked" />

@code {
    bool isChecked;
}
```

コンポーネントがレンダリングされると、チェックボックスの値が`isChecked`フィールドの値に設定されます。 ユーザーがチェックボックスをオンにする`onchange`と、イベントが発生`isChecked`し、フィールドが新しい値に設定されます。 この`@bind`場合の構文は、次のマークアップに相当します。

```razor
<input value="@isChecked" @onchange="(UIChangeEventArgs e) => isChecked = e.Value" />
```

バインドに使用するイベントを変更するには、 `@bind:event`属性を使用します。

```razor
<input @bind="text" @bind:event="oninput" />
<p>@text</p>

@code {
    string text;
}
```

コンポーネントは、パラメーターへのデータバインディングをサポートすることもできます。 データバインドには、バインド可能なパラメーターと同じ名前のイベントコールバックパラメーターを定義します。 "Changed" サフィックスが名前に追加されます。

*PasswordBox。 razor*

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

データバインディングを基になる UI 要素に連結するには、 `@bind`属性を使用するのではなく、値を設定し、ui 要素のイベントを直接処理します。

コンポーネントパラメーターにバインドするには、 `@bind-{Parameter}`属性を使用して、バインド先のパラメーターを指定します。

```razor
<PasswordBox @bind-Password="password" />

@code {
    string password;
}
```

## <a name="state-changes"></a>状態変更

コンポーネントの状態が通常の UI イベントまたはイベントコールバックの外部で変更された場合、コンポーネントは、再レンダリングが必要であることを手動で通知する必要があります。 コンポーネントの状態が変更されたことを通知する`StateHasChanged`には、コンポーネントでメソッドを呼び出します。

次の例では、コンポーネントによって、アプリ`AppState`の他の部分で更新可能なサービスからのメッセージが表示されます。 コンポーネントは、メッセージ`StateHasChanged`が更新さ`AppState.OnChange`れるたびにコンポーネントがレンダリングされるように、そのメソッドをイベントに登録します。

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

ASP.NET Web Forms framework には、モジュール、ページ、およびコントロールに対して明確に定義されたライフサイクルメソッドがあります。 たとえば、次のコントロールは`Init`、、 `Load`、および`UnLoad`の各ライフサイクルイベントのイベントハンドラーを実装します。

*Counter.ascx.cs*

```csharp
public partial class Counter : System.Web.UI.UserControl
{
    protected void Page_Init(object sender, EventArgs e) { ... }
    protected void Page_Load(object sender, EventArgs e) { ... }
    protected void Page_UnLoad(object sender, EventArgs e) { ... }
}
```

Blazor コンポーネントにも、明確に定義されたライフサイクルがあります。 コンポーネントのライフサイクルは、コンポーネントの状態を初期化し、高度なコンポーネントの動作を実装するために使用できます。

すべての Blazor のコンポーネントライフサイクルメソッドには、同期バージョンと非同期バージョンの両方があります。 コンポーネントのレンダリングは同期です。 コンポーネントレンダリングの一部として非同期ロジックを実行することはできません。 すべての非同期ロジックは、 `async`ライフサイクルメソッドの一部として実行する必要があります。

### <a name="oninitialized"></a>OnInitialized 化

コンポーネント`OnInitialized`を`OnInitializedAsync`初期化するには、メソッドとメソッドを使用します。 コンポーネントは通常、最初のレンダリング後に初期化されます。 コンポーネントが初期化されると、最終的に破棄される前に複数回レンダリングされる可能性があります。 メソッド`OnInitialized`は、ASP.NET Web フォーム`Page_Load`のページおよびコントロールのイベントに似ています。

```csharp
protected override void OnInitialized() { ... }
protected override async Task OnInitializedAsync() { await ... }
```

### <a name="onparametersset"></a>OnParametersSet

コンポーネント`OnParametersSet`が`OnParametersSetAsync`親からパラメーターを受け取り、値がプロパティに割り当てられるときに、メソッドとメソッドが呼び出されます。 これらのメソッドは、コンポーネントの初期化の後、および*コンポーネントがレンダリング*されるたびに実行されます。

```csharp
protected override void OnParametersSet() { ... }
protected override async Task OnParametersSetAsync() { await ... }
```

### <a name="onafterrender"></a>OnAfterRender

メソッド`OnAfterRender`と`OnAfterRenderAsync`メソッドは、コンポーネントのレンダリングが完了した後に呼び出されます。 この時点で、要素参照とコンポーネント参照が設定されます (以下の概念を参照)。 この時点では、ブラウザーとの対話機能が有効になっています。 DOM および JavaScript の実行とのやり取りは、安全に実行できます。

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

`OnAfterRender``OnAfterRenderAsync` *サーバーでのプリレンダリング時には呼び出されませ*ん。

`firstRender`パラメーターは、 `true`コンポーネントが初めてレンダリングされるときに実行されます。それ以外の場合、 `false`その値はです。

### <a name="idisposable"></a>IDisposable

Blazor コンポーネントは、 `IDisposable` UI からコンポーネントが削除されたときに、リソースを破棄するためにを実装できます。 Razor コンポーネントは、 `IDispose` `@implements`ディレクティブを使用してを実装できます。

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

ASP.NET Web フォームでは、ID を参照することによって、コントロールインスタンスをコード内で直接操作するのが一般的です。 Blazor では、コンポーネントへの参照をキャプチャして操作することもできますが、これはあまり一般的ではありません。

Blazor でコンポーネント参照をキャプチャするには、 `@ref`ディレクティブ属性を使用します。 属性の値は、参照されるコンポーネントと同じ型の設定可能フィールドの名前と一致している必要があります。

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

親コンポーネントがレンダリングされると、そのフィールドに子コンポーネントインスタンスが設定されます。 その後、コンポーネントインスタンスのメソッドを呼び出したり、それ以外の操作を行ったりすることができます。

コンポーネント参照を使用してコンポーネントの状態を直接操作することは推奨されません。 これにより、コンポーネントが適切な時刻に自動的にレンダリングされるのを防ぐことができます。

## <a name="capture-element-references"></a>要素参照のキャプチャ

Blazor コンポーネントは、要素への参照をキャプチャできます。 ASP.NET Web フォームの HTML サーバーコントロールとは異なり、Blazor の要素参照を使用して DOM を直接操作することはできません。 Blazor は DOM 比較アルゴリズムを使用して、ほとんどの DOM 対話を処理します。 Blazor でキャプチャされた要素参照は不透明です。 ただし、JavaScript の相互運用呼び出しで特定の要素参照を渡すために使用されます。 JavaScript の相互運用機能の詳細については、「 [ASP.NET Core Blazor javascript interop](/aspnet/core/blazor/javascript-interop)」を参照してください。

## <a name="templated-components"></a>テンプレート コンポーネント

ASP.NET Web フォームでは、テンプレート化された*コントロール*を作成できます。 開発者は、テンプレート化されたコントロールを使用して、コンテナーコントロールの表示に使用する HTML の一部を指定できます。 テンプレート化されたサーバーコントロールを構築するメカニズムは複雑ですが、ユーザーがカスタマイズ可能な方法でデータを表示するための強力なシナリオを実現します。 テンプレート化された`Repeater`コントロール`DataList`の例として、やがあります。

Blazor コンポーネントは、型または`RenderFragment` `RenderFragment<T>`型のコンポーネントパラメーターを定義することによって、テンプレートを設定することもできます。 は`RenderFragment` 、コンポーネントによってレンダリングできる Razor マークアップのチャンクを表します。 `RenderFragment<T>`は、レンダリングフラグメントのレンダリング時に指定できるパラメーターを受け取る Razor マークアップのチャンクです。

### <a name="child-content"></a>子コンテンツ

Blazor コンポーネントは、 `RenderFragment`子コンテンツをとしてキャプチャし、コンポーネントレンダリングの一部としてそのコンテンツをレンダリングできます。 子コンテンツをキャプチャするには、型`RenderFragment`のコンポーネントパラメーターを定義`ChildContent`し、という名前を指定します。

*ChildContentComponent。 razor*

```razor
<h1>Component with child content</h1>

<div>@ChildContent</div>

@code {
    [Parameter]
    public RenderFragment ChildContent { get; set; }
}
```

親コンポーネントは、通常の Razor 構文を使用して子コンテンツを提供できます。

```razor
<ChildContentComponent>
    <p>The time is @DateTime.Now</p>
</ChildContentComponent>
```

### <a name="template-parameters"></a>テンプレート パラメーター

また、テンプレート化 Blazor コンポーネントでは、型または`RenderFragment` `RenderFragment<T>`型の複数のコンポーネントパラメーターを定義することもできます。 のパラメーターは、 `RenderFragment<T>`呼び出されたときに指定できます。 コンポーネントのジェネリック型パラメーターを指定するには、 `@typeparam` Razor ディレクティブを使用します。

*SimpleListView。 razor*

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

テンプレート化されたコンポーネントを使用する場合、テンプレートパラメーターは、パラメーターの名前と一致する子要素を使用して指定できます。 要素として`RenderFragment<T>`渡される型のコンポーネント引数には`context`、という名前の暗黙的なパラメーターがあります。 子要素の`Context`属性を使用して、この実装パラメーターの名前を変更できます。 ジェネリック型パラメーターは、型パラメーターの名前と一致する属性を使用して指定できます。 可能な場合は、型パラメーターが推論されます。

```razor
<SimpleListView Items="messages" TItem="string">
    <Heading>
        <h1>My list</h1>
    </Heading>
    <ItemTemplate Context="message">
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

Blazor コンポーネントは、通常、単一の*razor*ファイルで作成されます。 ただし、分離コードファイルを使用して、コードとマークアップを分離することもできます。 コンポーネントファイルを使用するには、コンポーネントファイルのファイル名と一致し、 *.cs*拡張子を追加した C# ファイルを追加します (*Counter.razor.cs*)。 コンポーネントの基本クラスを定義するには、C# ファイルを使用します。 基底クラスには任意の名前を指定できますが、クラスにはコンポーネントクラスと同じ名前を付けますが、 `Base`拡張機能が追加され`CounterBase`ます ()。 コンポーネントベースのクラスも、から`ComponentBase`派生する必要があります。 次に、Razor コンポーネントファイルで、 `@inherits`ディレクティブを追加して、コンポーネントの基本クラスを指定`@inherits CounterBase`します ()。

*カウンタ。 razor*

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

基底クラスのコンポーネントのメンバーの可視性は、コンポーネントクラス`protected`に`public`表示される必要があります。

## <a name="additional-resources"></a>その他のリソース

前のは、Blazor コンポーネントのすべての側面を網羅するものではありません。 [ASP.NET Core Razor コンポーネントを作成して使用](/aspnet/core/blazor/components)する方法の詳細については、Blazor のドキュメントを参照してください。

>[!div class="step-by-step"]
>[前へ](app-startup.md)
>[次へ](pages-routing-layouts.md)
