---
title: キーワード リファレンス
description: すべての F# 言語のキーワードに関する情報へのリンクを検索します。
ms.date: 05/16/2016
ms.openlocfilehash: d55846fe7c8d31454b6bc8684de75546800df7d6
ms.sourcegitcommit: 69bf8b719d4c289eec7b45336d0b933dd7927841
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2019
ms.locfileid: "57845295"
---
# <a name="keyword-reference"></a>キーワード リファレンス

このトピックでには、F# 言語のすべてのキーワードについての情報へのリンクが含まれています。

## <a name="f-keyword-table"></a>F#キーワードのテーブル

次の表は、簡単な説明と詳細が含まれている関連するトピックへのリンクと共に、アルファベット順に、F# のすべてのキーワードを示します。

|キーワード|リンク|説明|
|-------|----|-----------|
|`abstract`|[メンバー](members/index.md)<br /><br />[抽象クラス](abstract-classes.md)|宣言されているか、仮想で既定の実装を備えた型の実装を持つかないメソッドを示します。|
|`and`|[`let` バインド](functions/let-bindings.md)<br /><br />[レコード](records.md)<br /><br />[メンバー](members/index.md)<br /><br />[制約](generics/constraints.md)|再帰的なバインドとレコードをジェネリック パラメーターで複数の制約を使用してプロパティの宣言で相互にで使用されます。|
|`as`|[クラス](classes.md)<br /><br />[パターン一致](Pattern-Matching.md)|現在のクラス オブジェクトにオブジェクト名を提供するために使用します。 パターン マッチング内のパターン全体に名前を指定するために使用します。|
|`assert`|[アサーション](assertions.md)|デバッグ中にコードを確認するために使用します。|
|`base`|[クラス](classes.md)<br /><br />[継承](inheritance.md)|基底クラスのオブジェクトの名前として使用されます。|
|`begin`|[冗語構文](verbose-syntax.md)|詳細な構文では、コード ブロックの開始を示します。|
|`class`|[クラス](classes.md)|詳細な構文では、クラス定義の先頭を示します。|
|`default`|[メンバー](members/index.md)|抽象メソッドの実装を示します抽象メソッドの宣言と共に使用すると、仮想メソッドを作成します。|
|`delegate`|[デリゲート](delegates.md)|デリゲートを宣言するために使用します。|
|`do`|[do バインド](functions/do-bindings.md)<br /><br />[ループ:`for...to` 式](loops-for-to-expression.md)<br /><br />[ループ:`for...in` 式](loops-for-in-expression.md)<br /><br />[ループ:`while...do` 式](loops-while-do-expression.md)|ループ構造で、または命令型コードを実行するために使用します。|
|`done`|[冗語構文](verbose-syntax.md)|冗語構文は、ループの式のコードのブロックの末尾を示します。|
|`downcast`|[キャストと変換](casting-and-conversions.md)|継承チェーンの下位にある型に変換するために使用します。|
|`downto`|[ループ:`for...to` 式](loops-for-to-expression.md)|`for`式では逆の順序でカウントする場合に使用します。|
|`elif`|[条件式: `if...then...else`](conditional-expressions-if-then-else.md)|条件付き分岐で使用されます。 短い形式`else if`します。|
|`else`|[条件式: `if...then...else`](conditional-expressions-if-then-else.md)|条件付き分岐で使用されます。|
|`end`|[構造体](structures.md)<br /><br />[判別共用体](discriminated-unions.md)<br /><br />[レコード](records.md)<br /><br />[型拡張](type-extensions.md)<br /><br />[冗語構文](verbose-syntax.md)|型の定義と型の拡張機能では、メンバーの定義のセクションの末尾を示します。<br /><br />始まるコード ブロックの末尾を指定するために使用の詳細な構文で、`begin`キーワード。|
|`exception`|[例外処理](exception-handling/index.md)<br /><br />[例外の種類](exception-handling/exception-types.md)|例外の種類を宣言するために使用します。|
|`extern`|[外部関数](functions/external-functions.md)|宣言されたプログラム要素が別のアセンブリまたはバイナリで定義されていることを示します。|
|`false`|[プリミティブ型](primitive-types.md)|ブール型リテラルとして使用されます。|
|`finally`|[例外処理:`try...finally`式](exception-handling/the-try-finally-expression.md)|組み合わせて使用`try`例外が発生したかどうかに関係なく実行されるコードのブロックを紹介します。|
|`fixed`|[修正しました](fixed.md)|ガベージ コレクションの対象を防ぐためにスタックにポインターを「固定」するために使用します。|
|`for`|[ループ:`for...to` 式](loops-for-to-expression.md)<br /><br />[ループ: for...in 式](loops-for-in-expression.md)|ループ構造で使用されます。|
|`fun`|[ラムダ式:`fun`キーワード](functions/lambda-expressions-the-fun-keyword.md)|ラムダ式、匿名とも呼ばれる関数で使用されます。|
|`function`|[match 式](match-expressions.md)<br /><br />[ラムダ式:Fun キーワード](functions/lambda-expressions-the-fun-keyword.md)|使用する代わりに短い、`fun`キーワードと`match`を 1 つの引数に一致するパターンを持つラムダ式の式。|
|`global`|[名前空間](namespaces.md)|最上位レベルの .NET 名前空間を参照するために使用します。|
|`if`|[条件式: `if...then...else`](conditional-expressions-if-then-else.md)|条件付き分岐構造で使用されます。|
|`in`|[ループ: for...in 式](loops-for-in-expression.md)<br /><br />[冗語構文](verbose-syntax.md)|バインディングから式を区切るためには、式のシーケンスと冗語構文を使用します。|
|`inherit`|[継承](inheritance.md)|基底クラスまたは基本インターフェイスを指定するために使用します。|
|`inline`|[関数](functions/index.md)<br /><br />[インライン関数](functions/inline-functions.md)|呼び出し元のコードに直接統合される関数を示すために使用します。|
|`interface`|[インターフェイス](interfaces.md)|宣言し、インターフェイスを実装するために使用します。|
|`internal`|[アクセス制御](access-control.md)|メンバーが表示されていることを指定するために使用ではなく外では、アセンブリ内部。|
|`lazy`|[遅延式](lazy-expressions.md)|結果が必要な場合にのみ実行される式を指定するために使用します。|
|`let`|[`let` バインド](functions/let-bindings.md)|関連付けるには、またはバインドして、値または関数の名前に使用します。|
|`let!`|[非同期ワークフロー](asynchronous-workflows.md)<br /><br />[コンピュテーション式](computation-expressions.md)|非同期計算の結果に名前をバインドする非同期のワークフローまたは計算型の結果に名前をバインドするために使用、その他のコンピュテーション式を使用します。|
|`match`|[match 式](match-expressions.md)|値をパターンと比較して分岐を使用します。|
|`match!`|[コンピュテーション式](computation-expressions.md#match)|その結果の計算式とパターン一致への呼び出しを使用をインライン化します。|
|`member`|[メンバー](members/index.md)|プロパティまたはオブジェクトの種類のメソッドを宣言するために使用します。|
|`module`|[モジュール](modules.md)|名前を他のコードから論理的に分離するには、関連する型、値、および関数のグループに関連付けるために使用します。|
|`mutable`|[let バインド](functions/let-bindings.md)|変更可能な値は、変数を宣言するために使用します。|
|`namespace`|[名前空間](namespaces.md)|他のコードから論理的に分離するには、関連する型とモジュールの名前を関連付けるために使用します。|
|`new`|[コンストラクター](members/constructors.md)<br /><br />[制約](generics/constraints.md)|宣言に使用すると、定義、またはコンス トラクターを作成するか、オブジェクトを作成することができます。<br /><br />ジェネリック パラメーターの制約を使用して型が特定のコンス トラクターを持つ必要があるかを指定しても。|
|`not`|[シンボルと演算子のリファレンス](symbol-and-operator-reference/index.md)<br /><br />[制約](generics/constraints.md)|実際にはキーワードです。 ただし、`not struct`組み合わせでは、ジェネリック パラメーターの制約として使用します。|
|`null`|[null 値](values/null-values.md)<br /><br />[制約](generics/constraints.md)|オブジェクトがないことを示します。<br /><br />ジェネリック パラメーターの制約にも使用されます。|
|`of`|[判別共用体](discriminated-unions.md)<br /><br />[デリゲート](delegates.md)<br /><br />[例外の種類](exception-handling/exception-types.md)|値のカテゴリの種類を示すために、判別共用体およびデリゲートと例外の宣言を使用します。|
|`open`|[インポート宣言: `open`キーワード](import-declarations-the-open-keyword.md)|修飾なしの名前空間またはモジュールの内容を利用するために使用します。|
|`or`|[シンボルと演算子のリファレンス](symbol-and-operator-reference/index.md)<br /><br />[制約](generics/constraints.md)|ブール値としてブール条件で使用される`or`演算子。 これは、`||` に相当します。<br /><br />メンバー制約でも使用されます。|
|`override`|[メンバー](members/index.md)|基本のバージョンとは異なる抽象または仮想メソッドのバージョンを実装するために使用します。|
|`private`|[アクセス制御](access-control.md)|同じ型またはモジュール内のコードにメンバーへのアクセスを制限します。|
|`public`|[アクセス制御](access-control.md)|型の外部からのメンバーにアクセスをできます。|
|`rec`|[関数](functions/index.md)|関数が再帰的であることを示すために使用します。|
|`return`|[非同期ワークフロー](Asynchronous-Workflows.md)<br /><br />[コンピュテーション式](computation-expressions.md)|コンピュテーション式の結果として提供する値を示すために使用します。|
|`return!`|[コンピュテーション式](computation-expressions.md)<br /><br />[非同期ワークフロー](asynchronous-workflows.md)|コンピュテーション式を示すために使用するには、評価されると、親のコンピュテーション式の結果を提供します。|
|`select`|[クエリ式](query-expressions.md)|クエリ式で使用すると、どのようなフィールドまたは列を抽出するを指定します。 コンテキスト キーワード、つまり実際に予約語ではないと適切なコンテキストでのキーワードに似た動作のみであるに注意してください。|
|`static`|[メンバー](members/index.md)|メソッドや型のインスタンスなしで呼び出されるプロパティまたは型のすべてのインスタンス間で共有される値のメンバーを示すために使用します。|
|`struct`|[構造体](structures.md)<br /><br /> [タプル](tuples.md)<br/><br/>[制約](generics/constraints.md)|構造体の型を宣言するために使用します。<br /><br/>構造体タプルを指定するために使用します。<br/><br />ジェネリック パラメーターの制約にも使用されます。<br /><br />OCaml モジュールの定義の互換性のために使用します。|
|`then`|[条件式: `if...then...else`](conditional-expressions-if-then-else.md)<br /><br />[コンストラクター](members/constructors.md)|条件式で使用されます。<br /><br />オブジェクトの構築後に副作用を実行するために使用します。|
|`to`|[ループ:`for...to` 式](loops-for-to-expression.md)|使用される`for`ループ範囲を示します。|
|`true`|[プリミティブ型](primitive-types.md)|ブール型リテラルとして使用されます。|
|`try`|[例外処理:Try...with 式](exception-handling/the-try-with-expression.md)<br /><br />[例外処理:Try... 最後に式](exception-handling/the-try-finally-expression.md)|例外を生成するコードのブロックを導入するために使用します。 組み合わせて使用`with`または`finally`します。|
|`type`|[F# の型](fsharp-types.md)<br /><br />[クラス](classes.md)<br /><br />[レコード](records.md)<br /><br />[構造体](structures.md)<br /><br />[列挙型](enumerations.md)<br /><br />[判別共用体](discriminated-unions.md)<br /><br />[型略称](type-abbreviations.md)<br /><br />[測定単位](units-of-measure.md)|クラス、レコード、構造、判別共用体、列挙型、長さの単位を宣言するか省略形を入力するために使用します。|
|`upcast`|[キャストと変換](casting-and-conversions.md)|上位の継承チェーンにある型に変換するために使用します。|
|`use`|[リソースの管理:`use`キーワード](resource-management-the-use-keyword.md)|代わりに使用`let`を必要とする値の`Dispose`リソースを解放するために呼び出します。|
|`use!`|[コンピュテーション式](computation-expressions.md)<br /><br />[非同期ワークフロー](asynchronous-workflows.md)|代わりに使用`let!`非同期ワークフローで必要な値には、その他のコンピュテーション式`Dispose`リソースを解放するために呼び出します。|
|`val`|[明示的なフィールド: `val`キーワード](members/explicit-fields-the-val-keyword.md)<br /><br />[シグネチャ](signatures.md)<br /><br />[メンバー](members/index.md)|値を示すに署名または限られた状況で、メンバーを宣言する型を使用します。|
|`void`|[プリミティブ型](primitive-types.md)|.NET を示す`void`型。 その他の .NET 言語と相互運用するときに使用されます。|
|`when`|[制約](generics/constraints.md)|ブール条件の使用 (*とガード*) パターン一致、およびジェネリック型パラメーターの制約句を導入します。|
|`while`|[ループ:`while...do` 式](loops-while-do-expression.md)|ループ構造が導入されています。|
|`with`|[match 式](match-expressions.md)<br /><br />[オブジェクト式](object-expressions.md)<br /><br />[レコード式のコピーと更新](copy-and-update-record-expressions.md)<br /><br />[型拡張](type-extensions.md)<br /><br />[例外処理:`try...with`式](exception-handling/the-try-with-expression.md)|と共に使用される、`match`パターン マッチング式のキーワード。 オブジェクトの式でも使用し、レコードのコピーの式、メンバーの定義を紹介し、例外ハンドラーを導入する拡張機能を入力します。|
|`yield`|[シーケンス](sequences.md)|シーケンスの値を生成するために、シーケンス式で使用します。|
|`yield!`|[コンピュテーション式](computation-expressions.md)<br /><br />[非同期ワークフロー](asynchronous-workflows.md)|コンピュテーション式で指定された計算式の結果を含むコンピュテーション式の結果のコレクションに追加するために使用します。|

次のトークンでは、OCaml 言語のキーワードであるために、F# で予約されています。

* `asr`
* `land`
* `lor`
* `lsl`
* `lsr`
* `lxor`
* `mod`
* `sig`

使用する場合、`--mlcompatibility`コンパイラ オプションは、上記のキーワードが使用可能な識別子として。

次のトークンは、F# 言語の将来の拡張のキーワードとして予約されています。

* `atomic`
* `break`
* `checked`
* `component`
* `const`
* `constraint`
* `constructor`
* `continue`
* `eager`
* `event`
* `external`
* `functor`
* `include`
* `method`
* `mixin`
* `object`
* `parallel`
* `process`
* `protected`
* `pure`
* `sealed`
* `tailcall`
* `trait`
* `virtual`
* `volatile`

## <a name="see-also"></a>関連項目

- [F# 言語リファレンス](index.md)
- [シンボルと演算子のリファレンス](symbol-and-operator-reference/index.md)
- [コンパイラ オプション](compiler-options.md)
