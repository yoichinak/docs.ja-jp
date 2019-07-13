---
title: イベント
description: 学習方法F#イベントには、GUI プログラミングの重要なユーザー アクションと関数の呼び出しを関連付けることが有効にします。
ms.date: 05/16/2016
ms.openlocfilehash: ad2e8001b81f48fdeb783bee2423a3dc9e22ac79
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65645222"
---
# <a name="events"></a>イベント

> [!NOTE]
> この記事の API リファレンスのリンクをクリックすると MSDN に移動します。  docs.microsoft.com API リファレンスは完全ではありません。

イベントを使用すると、関数呼び出しをユーザーによる操作に関連付けることができます。イベントは、GUI プログラミングの重要な要素です。 イベントは、アプリケーションまたはオペレーティング システムによってトリガーすることもできます。

## <a name="handling-events"></a>イベントの処理

Windows フォームや WPF (Windows Presentation Foundation) などの GUI ライブラリを使用する場合、アプリケーションのコードの大半は、ライブラリによって定義されたイベントに応答して実行されます。 これらの定義済みイベントは、フォームやコントロールなどの GUI クラスのメンバーです。 ボタン クリックなどの既存のイベントにカスタム動作を追加するには、次のコードに示すように、目的の名前付きイベント (たとえば、`Click` クラスの `Form` イベント) を参照し、`Add` メソッドを呼び出します。 F# Interactive からこれを実行する場合は、`System.Windows.Forms.Application.Run(System.Windows.Forms.Form)` の呼び出しを省略します。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3601.fs)]

`Add` メソッドの型は、`('a -> unit) -> unit` です。 したがって、イベント ハンドラー メソッドは、1 つのパラメーター (通常はイベント引数) を受け取り、`unit` を返します。 前の例は、ラムダ式としてのイベント ハンドラーを示しています。 イベント ハンドラーは、次のコード例に示すように、関数値である場合もあります。 次のコード例は、イベントの種類に固有の情報を提供するイベント ハンドラー パラメーターの使い方も示しています。 `MouseMove` イベントの場合、システムはポインターの `System.Windows.Forms.MouseEventArgs` 位置および `X` 位置を含む `Y` オブジェクトを渡します。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3602.fs)]

## <a name="creating-custom-events"></a>カスタム イベントの作成

F# イベントは、F# で表されます[イベント](https://msdn.microsoft.com/library/f3b47c8a-4ee5-4ce8-9a72-ad305a17c4b9)クラスを実装、 [IEvent](https://msdn.microsoft.com/library/8dbca0df-f8a1-40bd-8d50-aa26f6a8b862)インターフェイス。 `IEvent` その他の 2 つのインターフェイスの機能を結合するインターフェイス自体は`System.IObservable<'T>`と[IDelegateEvent](https://msdn.microsoft.com/library/3d849465-6b8e-4fc5-b36c-2941d734268a)します。 したがって、`Event` は、他の言語のデリゲートに相当する機能と、`IObservable` からの追加機能を備えていることになります。つまり、F# のイベントでは、イベントのフィルター処理がサポートされるほか、F# のファースト クラスの関数とラムダ式をイベント ハンドラーとして使用できます。 この機能が提供される、[イベント モジュール](https://msdn.microsoft.com/library/8b883baa-a460-4840-9baa-de8260351bc7)します。

他の任意の .NET Framework イベントと同様に動作するイベントをクラスに作成するには、`Event` をクラス内のフィールドとして定義する `let` バインディングをクラスに追加します。 目的のイベント引数の型を型引数として指定することも、指定せずにコンパイラによって適切な型を推論することもできます。 CLI イベントとしてイベントを公開するイベント メンバーも定義する必要があります。 このメンバーには [CLIEvent](https://msdn.microsoft.com/library/d359f1dd-ffa5-42fb-8808-b4c8131a0333) 属性が必要です。 プロパティのように宣言されており、イベントの[発行](https://msdn.microsoft.com/library/b0fdaad5-25e5-43d0-9c0c-ce37c4aeb68e)プロパティを呼び出すだけで実装できます。 クラスのユーザーは、公開されたイベントの `Add` メソッドを使用してハンドラーを追加できます。 `Add` メソッドの引数はラムダ式にすることができます。 イベントの `Trigger` プロパティを使用すると、イベントを発生させて、引数をハンドラー関数に渡すことができます。 これを次のコード例に示します。 この例では、推論されているイベントの型引数はタプルで、ラムダ式の引数を表します。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3605.fs)]

出力は次のとおりです。

```
Event1 occurred! Object data: Hello World!
```

`Event` モジュールで提供される追加の機能を以下に示します。 次のコードは、`Event.create` の基本的な使用例を示しています。イベントおよびトリガー メソッドを作成し、ラムダ式の形式で 2 つのイベント ハンドラーを追加して、イベントを発生させて両方のラムダ式を実行します。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3603.fs)]

このコードの出力は、次のようになります。

```
Event occurred.
Given a value: Event occurred.
```

## <a name="processing-event-streams"></a>イベント ストリームの処理

使用して、イベントのイベント ハンドラーを追加するだけではなく、 [Event.add](https://msdn.microsoft.com/library/10670d3b-8d47-4f6e-b8df-ebc6f64ef4fd)関数で関数を使用することができます、`Event`モジュールの詳細にカスタマイズされた方法でイベントのストリームを処理します。 これを行うには、一連の関数呼び出しの最初の値として、イベントと共に前方パイプ (`|>`) を使用します。`Event` モジュールは、以降の関数呼び出しとして機能します。

特定の条件でのみ呼び出されるハンドラーを持つイベントを設定する方法を次のコード例に示します。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3604.fs)]

[Observable モジュール](https://msdn.microsoft.com/library/16b8610b-b30a-4df7-aa99-d9d352276227)観測可能なオブジェクトを操作するような関数が含まれています。 観測可能なオブジェクトはイベントに似ていますが、オブジェクト自体がサブスクライブされている場合にのみ、イベントをアクティブにサブスクライブします。

## <a name="implementing-an-interface-event"></a>インターフェイス イベントの実装

UI コンポーネントを開発するときは、多くの場合、まず、既存のフォームまたはコントロールを継承した新しいフォームまたはコントロールを作成します。 イベントは、しばしばインターフェイスで定義され、その場合、インターフェイスを実装してイベントを実装する必要があります。 `System.ComponentModel.INotifyPropertyChanged` インターフェイスは単一の `System.ComponentModel.INotifyPropertyChanged.PropertyChanged` イベントを定義します。 次のコードは、この継承されたインターフェイスで定義されたイベントを実装する方法を示します。

```fsharp
module CustomForm

open System.Windows.Forms
open System.ComponentModel

type AppForm() as this =
    inherit Form()

    // Define the propertyChanged event.
    let propertyChanged = Event<PropertyChangedEventHandler, PropertyChangedEventArgs>()
    let mutable underlyingValue = "text0"

    // Set up a click event to change the properties.
    do
        this.Click |> Event.add(fun evArgs -> this.Property1 <- "text2"
        this.Property2 <- "text3")

    // This property does not have the property-changed event set.
    member val Property1 : string = "text" with get, set

    // This property has the property-changed event set.
    member this.Property2
        with get() = underlyingValue
        and set(newValue) =
            underlyingValue <- newValue
            propertyChanged.Trigger(this, new PropertyChangedEventArgs("Property2"))

    // Expose the PropertyChanged event as a first class .NET event.
    [<CLIEvent>]
    member this.PropertyChanged = propertyChanged.Publish

    // Define the add and remove methods to implement this interface.
    interface INotifyPropertyChanged with
        member this.add_PropertyChanged(handler) = propertyChanged.Publish.AddHandler(handler)
        member this.remove_PropertyChanged(handler) = propertyChanged.Publish.RemoveHandler(handler)

    // This is the event-handler method.
    member this.OnPropertyChanged(args : PropertyChangedEventArgs) =
        let newProperty = this.GetType().GetProperty(args.PropertyName)
        let newValue = newProperty.GetValue(this :> obj) :?> string
        printfn "Property %s changed its value to %s" args.PropertyName newValue

// Create a form, hook up the event handler, and start the application.
let appForm = new AppForm()
let inpc = appForm :> INotifyPropertyChanged
inpc.PropertyChanged.Add(appForm.OnPropertyChanged)
Application.Run(appForm)
```

コンストラクターでイベントをフックアップする場合、イベント フックアップが追加のコンストラクターの `then` ブロックに存在する必要があるため、コードは次の例のように少し複雑になります。

```fsharp
module CustomForm

open System.Windows.Forms
open System.ComponentModel

// Create a private constructor with a dummy argument so that the public
// constructor can have no arguments.
type AppForm private (dummy) as this =
    inherit Form()

    // Define the propertyChanged event.
    let propertyChanged = Event<PropertyChangedEventHandler, PropertyChangedEventArgs>()
    let mutable underlyingValue = "text0"

    // Set up a click event to change the properties.
    do
        this.Click |> Event.add(fun evArgs -> this.Property1 <- "text2"
        this.Property2 <- "text3")

    // This property does not have the property changed event set.
    member val Property1 : string = "text" with get, set

    // This property has the property changed event set.
    member this.Property2
        with get() = underlyingValue
        and set(newValue) =
            underlyingValue <- newValue
            propertyChanged.Trigger(this, new PropertyChangedEventArgs("Property2"))

    [<CLIEvent>]
    member this.PropertyChanged = propertyChanged.Publish

    // Define the add and remove methods to implement this interface.
    interface INotifyPropertyChanged with
        member this.add_PropertyChanged(handler) = this.PropertyChanged.AddHandler(handler)
        member this.remove_PropertyChanged(handler) = this.PropertyChanged.RemoveHandler(handler)

    // This is the event handler method.
    member this.OnPropertyChanged(args : PropertyChangedEventArgs) =
        let newProperty = this.GetType().GetProperty(args.PropertyName)
        let newValue = newProperty.GetValue(this :> obj) :?> string
        printfn "Property %s changed its value to %s" args.PropertyName newValue

    new() as this =
        new AppForm(0)
        then
            let inpc = this :> INotifyPropertyChanged
            inpc.PropertyChanged.Add(this.OnPropertyChanged)

// Create a form, hook up the event handler, and start the application.
let appForm = new AppForm()
Application.Run(appForm)
```

## <a name="see-also"></a>関連項目

- [メンバー](index.md)
- [処理とイベントの発生](../../../../docs/standard/events/index.md)
- [ラムダ式:`fun`キーワード](../functions/lambda-expressions-the-fun-keyword.md)
- [Control.Event モジュール](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.event-module-%5bfsharp%5d)
- [Control.Event&#60;' T&#62;クラス](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.event%5b%27t%5d-class-%5bfsharp%5d)
- [Control.Event&#60;'Delegate'、Args&#62;クラス](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.event%5b%27delegate%2c%27args%5d-class-%5bfsharp%5d)
