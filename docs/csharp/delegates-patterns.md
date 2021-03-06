---
title: "デリゲートの一般的なパターン"
description: "コンポーネント間の密接な結合を避けるための、コードでのデリゲートの一般的な使用パターンについて説明します。"
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 0ff8fdfd-6a11-4327-b061-0f2526f35b43
ms.openlocfilehash: 83214800fb997e9274cacfd1bae85ab07c4515a2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="common-patterns-for-delegates"></a>デリゲートの一般的なパターン

[前へ](delegates-strongly-typed.md)

デリゲートは、コンポーネント間の結合度を最小限にしたソフトウェア設計を可能にするメカニズムです。

この種の設計の代表的な例が LINQ です。 LINQ のクエリ式パターンは、そのすべての機能がデリゲートによって支えられています。 簡単な例を考えてみましょう。

```csharp
var smallNumbers = numbers.Where(n => n < 10);
```

このコードは、一連の数値から値が 10 未満である数値のみを抽出するものです。
`Where` メソッドは、デリゲートを使って、どの要素を抽出するかを判断しています。 LINQ クエリを作成するとき、その具体的な目的に合ったデリゲートの機能は、皆さんが実装することになります。

Where メソッドのプロトタイプは次のとおりです。

```csharp
public static IEnumerable<TSource> Where<in TSource> (IEnumerable<TSource> source, Func<TSource, bool> predicate);
```

この例は、LINQ のすべてのメソッドに当てはまります。 具体的なクエリを扱うコードには、すべてデリゲートが使われているのです。 きわめて強力な API デザイン パターンなので、しっかり覚えて自分のものにしてください。

この単純な例から、コンポーネント間の結合関係がデリゲートにはほとんど必要ないことがわかります。 特定の基本クラスから派生したクラスを作成する必要がないのです。 特定のインターフェイスを実装する必要もありません。
唯一の要件は、目的のタスクに必要なメソッドの機能を 1 つ、手の届くところに実装するだけです。

## <a name="building-your-own-components-with-delegates"></a>デリゲートを使った独自のコンポーネントを作成する

この例を踏まえて、デリゲートを利用した設計を使ってコンポーネントを作成してみましょう。

たとえば大規模なシステムのログ メッセージに使われるコンポーネントとは、どのようなものでしょうか。 そのライブラリ コンポーネントは、各種プラットフォーム上のさまざまな環境で使われることが考えられます。 ログを扱うコンポーネントには、共通する機能が多数存在します。 まず、システム内のコンポーネントからメッセージを受け取らなければなりません。 それらのメッセージには、さまざまな優先度が割り当てられ、中心となるコンポーネントがそれらの優先度を管理できるようになっていることでしょう。 最終的にアーカイブされるメッセージの形式には、タイムスタンプが記録されている必要があります。 さらに高度な用途としては、ログの発生元のコンポーネントごとにメッセージをフィルタリングすることも考えられます。

この機能には、不確定要素が 1 つあります。メッセージがどこに出力されるかです。 メッセージがエラー コンソールに出力されるか、 ファイルに出力されるかは、環境によってさまざまです。 データベース ストレージや OS のイベント ログのほか、ドキュメント ストレージに出力される可能性もあります。

また複数の場所に出力して、それぞれ異なる用途に使われるようなケースもあります。 たとえばコンソールとファイルにメッセージを出力したい場合もあるでしょう。

デリゲートを使った設計なら運用の幅が大きく広がり、将来追加される可能性のあるストレージ メカニズムへの対応が容易になります。

この設計の下では、主要なログ コンポーネントが必ずしも仮想クラスである必要はなく、シール クラスであってもかまいません。 一連のデリゲートを組み込めば、さまざまなストレージ メディアにメッセージを書き込むことができます。 マルチキャスト デリゲートがネイティブでサポートされているため、メッセージを複数の場所 (ファイルとコンソールなど) に出力する必要のある状況にも簡単に対応することができます。

## <a name="a-first-implementation"></a>初めての実装

最初は簡単な機能を実装してみましょう。新しいメッセージを受け取ったら、アタッチされたデリゲートを使ってそれらを出力するものです。 まず、コンソールにメッセージを出力するデリゲートを 1 つ作成します。

```csharp
public static class Logger
{
    public static Action<string> WriteMessage;
    
    public static void LogMessage(string msg)
    {
        WriteMessage(msg);
    }
}
```

上の静的クラスは、ごく簡単なコードですが、きちんと機能します。 メッセージをコンソールに出力するメソッドの機能を 1 つ実装する必要があります。 

```csharp
public static void LogToConsole(string message)
{
    Console.Error.WriteLine(message);
}
```

最後にそのメソッドを、Logger に宣言されている WriteMessage デリゲートにアタッチして接続する必要があります。

```csharp
Logger.WriteMessage += LogToConsole;
```

## <a name="practices"></a>実践

紹介したサンプルはごく簡単なものですが、デリゲートを伴う設計についての重要な指針がいくつか示されています。

ユーザーは、Core Framework に定義されているデリゲート型を使うことで、さらに簡単にデリゲートを扱うことができます。 皆さんが新しい型を定義する必要はなく、皆さんのライブラリを利用する開発者も、特別な目的を持ったデリゲート型を新たに覚える必要がありません。

使用されているインターフェイスはごくわずかでありながら、最大限の柔軟性が得られるようになっています。つまり新しい出力ロガーを作成するために皆さんがすべきことは、メソッドを 1 つ作成することです。 そのメソッドは静的メソッドでも、インスタンス メソッドでもかまいません。 またアクセス指定も任意です。

## <a name="formatting-output"></a>出力の初期設定

最初のコード例にもう少し肉付けしてみましょう。その後、別のログ メカニズムの作成に進みます。

まず、より構造化されたメッセージを作成するために、いくつかの引数を `LogMessage()` メソッドに追加します。

```csharp
// Logger implementation two
public enum Severity
{
    Verbose,
    Trace,
    Information,
    Warning,
    Error,
    Critical
}

public static class Logger
{
    public static Action<string> WriteMessage;
    
    public static void LogMessage(Severity s, string component, string msg)
    {
        var outputMsg = $"{DateTime.Now}\t{s}\t{component}\t{msg}";
        WriteMessage(outputMsg);
    }
}
```

次に、その `Severity` 引数を利用して、ログ出力に送るメッセージをフィルター選択します。 

```csharp
public static class Logger
{
    public static Action<string> WriteMessage;
    
    public static Severity LogLevel {get;set;} = Severity.Warning;
    
    public static void LogMessage(Severity s, string component, string msg)
    {
        if (s < LogLevel)
            return;
            
        var outputMsg = $"{DateTime.Now}\t{s}\t{component}\t{msg}";
        WriteMessage(outputMsg);
    }
}
```
## <a name="practices"></a>実践

ログのインフラストラクチャに新しい機能を追加しました。 このロガー コンポーネントは、出力メカニズムとの結び付きがきわめて弱いので、このように新しい機能を追加しても、ロガーのデリゲートを実装する側のコードには一切影響が生じません。

他の部分には変更を加えずに一部分だけをアップデートできるという点に関しては、このプログラム コードを記述していく過程で、結び付きの弱さによって運用の幅が広がる例が他にもたくさん見つかることでしょう。 実際、大規模なアプリケーションになると、ロガー出力クラスを別のアセンブリに置き、リビルドすら必要ないケースもあります。

## <a name="building-a-second-output-engine"></a>2 つ目の出力エンジンの作成

1 つ目のログ コンポーネントがうまく作成できました。 次は、メッセージをファイルに記録する出力エンジンを追加してみましょう。 この出力エンジンは、先ほどよりも少し複雑になります。 このクラスにはファイル操作がカプセル化され、毎回出力後に必ずファイルが閉じられます。 これによって、メッセージが生成されるたびにすべてのデータが確実にディスクにフラッシュされます。

このファイル ベースのロガーを次に示します。

```csharp
public class FileLogger
{
    private readonly string logPath;
    public FileLogger(string path)
    {
        logPath = path;
        Logger.WriteMessage += LogMessage;
    }
    
    public void DetachLog() => Logger.WriteMessage -= LogMessage;

    // make sure this can't throw.
    private void LogMessage(string msg)
    {
        try {
            using (var log = File.AppendText(logPath))
            {
                log.WriteLine(msg);
                log.Flush();
            }
        } catch (Exception e)
        {
            // Hmm. Not sure what to do.
            // Logging is failing...
        }
    }
}
```

このクラスを作成した後、インスタンス化すれば、その LogMessage メソッドを Logger コンポーネントにアタッチすることができます。

```csharp
var file = new FileLogger("log.txt");
```

この 2 つは、どちらか一方しか使えないというわけではありません。 両方のログ メソッドをアタッチすれば、コンソールとファイルにメッセージを生成することができます。

```csharp
var fileOutput = new FileLogger("log.txt");
Logger.WriteMessage += LogToConsole;
```

後で同じアプリケーションで、片方のデリゲートを削除しても、システムに問題が生じることはありません。

```csharp
Logger.WriteMessage -= LogToConsole;
```

## <a name="practices"></a>実践

ログ サブシステム用に 2 つ目の出力ハンドラーを追加しました。
こちらは、ファイル システムを正しくサポートするために、もう少しインフラストラクチャを整える必要があります。 デリゲートはインスタンス メソッドです。 プライベート メソッドでもあります。
それより広いアクセス指定は必要ありません。なぜならデリゲートの接続は、デリゲート インフラストラクチャが行ってくれるためです。

また、デリゲート ベースの設計では、新たにコードを書かなくても複数の出力メソッドを利用することができます。 複数の出力メソッドをサポートするために、別途インフラストラクチャを作成する必要はありません。 何もしなくても、呼び出しリストの中では、それらが別々のメソッドになるのです。

ファイル ロガーの出力メソッドのコードに注目してください。 決して例外がスローされないようにコーディングされています。 厳密には常に必要というわけではありませんが、通常はこのようにすることをお勧めします。 いずれかのデリゲート メソッドから例外がスローされた場合に、呼び出しリストに残っている他のデリゲートが呼び出されなくなってしまいます。

最後の注意点として、ファイル ロガーは、ログ メッセージごとにファイルを開閉することによって、そのリソースを自己管理する必要があります。 または、ファイルを開いたままにすることも可能です。つまり IDisposable を実装し、完了した時点でファイルを閉じるようにするのです。
どちらの方法にも長所と短所があります。 また、どちらの方法も、クラス間の結合度がわずかに増します。

しかし、どちらのシナリオをサポートするにしても、Logger クラスのコードには一切手を加える必要がありません。

## <a name="handling-null-delegates"></a>Null デリゲートの処理

最後に、出力メカニズムが選択されなかったケースに備えて、LogMessage メソッドに変更を加えたいと思います。 現在の実装コードでは、`WriteMessage` デリゲートに呼び出しリストがアタッチされなかった場合、`NullReferenceException` がスローされます。
メソッドがアタッチされていなくても、何事もなかったように処理が継続されるような設計の方が望ましい場合もあります。 これは、`Delegate.Invoke()` メソッドに null 条件演算子を組み合わせて使えば簡単に実現できます。

```csharp
public static void LogMessage(string msg)
{
    WriteMessage?.Invoke(msg);
}
```

null 条件演算子 (`?.`) は、左辺オペランド (このケースでは `WriteMessage`) が null のとき、そこで評価が打ち切られます。つまり、メッセージを記録する処理は試行されません。

`System.Delegate` や `System.MulticastDelegate` のドキュメントを探しても、`Invoke()` メソッドは記載されていません。 宣言されているデリゲート型には、コンパイラによってタイプ セーフな `Invoke` メソッドが生成されます。 つまり、この例では、`Invoke` が `string` 引数を 1 つ持ち、戻り値の型が void であるということです。

## <a name="summary-of-practices"></a>実践のまとめ

ログ コンポーネントの基本的概念を見てきました。この概念は、その他の出力機構や各種機能に応用することができます。 デリゲートを使った設計では、そうしたコンポーネント間の結びつきを疎に保つことができるのです。 これにはさまざまな利点があります。 まず、ごくわずかな手間で、新しい出力メカニズムを作成してシステムにアタッチすることができます。 新たに追加するメカニズムで必要となるのは、1 つのメソッドだけです。ログ メッセージを出力するメソッドです。 これは、新しい機能を追加するときに問題がきわめて起きにくい設計といえます。 どのような出力機構を追加するにせよ、求められるコントラクトはメソッドを 1 つ実装する、ということです。 それは静的メソッドでもインスタンス メソッドでもかまいません。 アクセスできる範囲も、public や private を含め、正当なアクセス指定であれば何でもかまいません。

Logger クラスには、これまでの動作を大きく変えることなく何度でも、その機能を強化したり変更を加えたりすることができます。 あらゆるクラスに言えることですが、パブリック API の変更には、互換性に影響する変更のリスクが伴います。 しかし、ロガーと出力エンジンとの結合はデリゲートを介してのみ行われるので、他の型 (インターフェイス、基本クラスなど) が関係してくることはありません。 その結合度は最小限で済むのです。

[次へ](events-overview.md)
