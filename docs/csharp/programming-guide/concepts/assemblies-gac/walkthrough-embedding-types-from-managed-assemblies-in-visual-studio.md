---
title: チュートリアル:Visual Studio でマネージド アセンブリからの型を埋め込む (C#)
ms.date: 07/20/2015
ms.assetid: 55ed13c9-c5bb-4bc2-bcd8-0587eb568864
ms.openlocfilehash: 5e6494f133128e3982aa07323d2c65b9fa5de47b
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595796"
---
# <a name="walkthrough-embedding-types-from-managed-assemblies-in-visual-studio-c"></a>チュートリアル:Visual Studio でマネージド アセンブリからの型を埋め込む (C#)

厳密な名前を持つマネージド アセンブリから型情報を埋め込むと、アプリケーション内で型を疎結合して、バージョンに依存しないプログラムを実現できます。 つまり、各バージョン用の再コンパイルを必要とすることなく、マネージド ライブラリの複数のバージョンから型を使用するプログラムを記述できます。

型の埋め込みは、COM 相互運用と共によく使用されます (Microsoft Office からのオートメーション オブジェクトを使用するアプリケーションなど)。 型情報を埋め込むと、同じビルドのプログラムを、別のコンピューター上にある別バージョンの Microsoft Office と連携させることができます。 ただし、型の埋め込みはフル マネージド ソリューションと共に使用することもできます。

型情報は、次の特性を持つアセンブリから埋め込むことができます。

- アセンブリが、少なくとも 1 つのパブリック インターフェイスを公開している。

- 埋め込みインターフェイスに `ComImport` 属性と `Guid` 属性 (および一意の GUID) が付けられている。

- アセンブリに、`ImportedFromTypeLib` 属性または `PrimaryInteropAssembly` 属性、およびアセンブリ レベルの `Guid` 属性が付けられている。 (既定では、アセンブリ レベルの `Guid` 属性は Visual C# プロジェクト テンプレートに含まれています。)

埋め込み可能なパブリック インターフェイスを指定したら、それらのインターフェイスを実装するランタイム クラスを作成できます。 その後、クライアント プログラムは、パブリック インターフェイスを含んだアセンブリを参照し、参照の `Embed Interop Types` プロパティを `True` に設定することで、デザイン時にそれらのインターフェイスの型情報を埋め込むことができます。 これは、コマンド ライン コンパイラを使用し、`/link` コンパイラ オプションを使用してアセンブリを参照することに相当します。 クライアント プログラムはその後、それらのインターフェイスとして型指定されたランタイム オブジェクトのインスタンスを読み込むことができます。 厳密な名前を持つランタイム アセンブリの新バージョンを作成した場合、クライアント プログラムを、更新後のランタイム アセンブリで再コンパイルする必要はありません。 クライアント プログラムでは、パブリック インターフェイスの埋め込み型情報を使用して、利用可能なバージョンをどちらでも引き続き使用できます。

型埋め込みの主な機能は、COM 相互運用アセンブリからの型情報の埋め込みをサポートすることなので、フル マネージドのソリューションで型情報を埋め込む場合には、次の制限が適用されます。

- COM 相互運用に固有の属性のみが埋め込まれます。その他の属性は無視されます。

- 型がジェネリック パラメーターを使用していて、ジェネリック パラメーターの型が埋め込み型である場合、その型はアセンブリの境界を越えて使用することはできません。 アセンブリの境界を越える場合の例としては、別のアセンブリからメソッドを呼び出す場合や、別のアセンブリで定義されている型から型を派生させる場合が挙げられます。

- 定数は埋め込まれません。

- <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> クラスでは、埋め込み型をキーとして利用できません。 埋め込み型をキーとしてサポートするために、独自のディクショナリ型を実装することは可能です。

このチュートリアルでは、次のタスクを行います。

- 埋め込み可能な型情報を含んだパブリック インターフェイスを持つ、厳密な名前付きのアセンブリを作成する。

- そのパブリック インターフェイスを実装する、厳密な名前付きのランタイム アセンブリを作成する。

- パブリック インターフェイスから型情報を埋め込み、ランタイム アセンブリからクラスのインスタンスを作成する、クライアント プログラムを作成する。

- ランタイム アセンブリを変更し、リビルドする。

- クライアント プログラムを実行して、新バージョンのランタイム アセンブリが、クライアント プログラムを再コンパイルしなくても使用されていることを確認する。

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="creating-an-interface"></a>インターフェイスの作成

#### <a name="to-create-the-type-equivalence-interface-project"></a>型等価性インターフェイス プロジェクトを作成するには

1. Visual Studio で、 **[ファイル]** メニューの **[新規作成]** をクリックし、 **[プロジェクト]** を選択します。

2. **[新しいプロジェクト]** ダイアログ ボックスの **[プロジェクトの種類]** ペインで、 **[Windows]** が選択されていることを確認します。 **[テンプレート]** ペインで **[クラス ライブラリ]** を選択します。 **[名前]** ボックスに `TypeEquivalenceInterface` と入力して、 **[OK]** をクリックします。 新しいプロジェクトが作成されます。

3. **ソリューション エクスプローラー**で、 Class1.cs ファイルを右クリックし、 **[名前の変更]** をクリックします。 ファイルの名前を `ISampleInterface.cs` に変更し、Enter キーを押します。 ファイルの名前を変更すると、クラスの名前も `ISampleInterface` に変更されます。 このクラスは、クラスのパブリック インターフェイスを表します。

4. TypeEquivalenceInterface プロジェクトを右クリックし、 **[プロパティ]** をクリックします。 **[ビルド]** タブをクリックします。開発用コンピューター上の有効な場所への出力パスを設定します (`C:\TypeEquivalenceSample` など)。 この場所は、このチュートリアルの後の手順でも使用されます。

5. プロジェクト プロパティの編集を続けたまま、 **[署名]** タブをクリックします。 **[アセンブリの署名]** オプションを選択します。 **[厳密な名前のキー ファイルを選択してください]** ボックスの一覧で **[\<新規作成...>]** をクリックします。 **[キー ファイル名]** ボックスに、「`key.snk`」と入力します。 **[キーファイルをパスワードで保護する]** チェック ボックスをオフにします。 Click **OK**.

6. ISampleInterface.cs ファイルを開きます。 ISampleInterface クラス ファイルに、ISampleInterface インターフェイスを作成するための次のコードを追加します。

    ```csharp
    using System;
    using System.Runtime.InteropServices;

    namespace TypeEquivalenceInterface
    {
        [ComImport]
        [Guid("8DA56996-A151-4136-B474-32784559F6DF")]
        public interface ISampleInterface
        {
            void GetUserInput();
            string UserInput { get; }
        }
    }
    ```

7. **[ツール]** メニューの **[GUID の作成]** をクリックします。 **[GUID の作成]** ダイアログ ボックスで、 **[レジストリ形式]** をクリックし、 **[コピー]** をクリックします。 **[終了]** をクリックします。

8. `Guid` 属性で、サンプルの GUID を削除し、 **[GUID の作成]** ダイアログ ボックスからコピーした GUID を貼り付けます。 コピーした GUID から中かっこ ({}) を削除します。

9. **ソリューション エクスプローラー**で、 **[プロパティ]** フォルダーを展開します。 AssemblyInfo.cs ファイルをダブルクリックします。 ファイルに次の属性を追加します。

    ```csharp
    [assembly: ImportedFromTypeLib("")]
    ```

     ファイルを保存します。

10. プロジェクトを保存します。

11. TypeEquivalenceInterface プロジェクトを右クリックし、 **[ビルド]** をクリックします。 クラス ライブラリの .dll ファイルがコンパイルされ、指定したビルド出力パス (たとえば、C:\TypeEquivalenceSample) に保存されます。

## <a name="creating-a-runtime-class"></a>ランタイム クラスの作成

#### <a name="to-create-the-type-equivalence-runtime-project"></a>型等価性ランタイム プロジェクトを作成するには

1. Visual Studio で、 **[ファイル]** メニューの **[新規作成]** をポイントし、 **[プロジェクト]** をクリックします。

2. **[新しいプロジェクト]** ダイアログ ボックスの **[プロジェクトの種類]** ペインで、 **[Windows]** が選択されていることを確認します。 **[テンプレート]** ペインで **[クラス ライブラリ]** を選択します。 **[名前]** ボックスに `TypeEquivalenceRuntime` と入力して、 **[OK]** をクリックします。 新しいプロジェクトが作成されます。

3. **ソリューション エクスプローラー**で、 Class1.cs ファイルを右クリックし、 **[名前の変更]** をクリックします。 ファイルの名前を `SampleClass.cs` に変更し、Enter キーを押します。 ファイルの名前を変更すると、クラスの名前も `SampleClass` に変更されます。 このクラスが `ISampleInterface` インターフェイスを実装します。

4. TypeEquivalenceRuntime プロジェクトを右クリックし、 **[プロパティ]** をクリックします。 **[ビルド]** タブをクリックします。出力パスを、TypeEquivalenceInterface プロジェクトで使用したのと同じ場所に設定します (たとえば、`C:\TypeEquivalenceSample`)。

5. プロジェクト プロパティの編集を続けたまま、 **[署名]** タブをクリックします。 **[アセンブリの署名]** オプションを選択します。 **[厳密な名前のキー ファイルを選択してください]** ボックスの一覧で **[\<新規作成...>]** をクリックします。 **[キー ファイル名]** ボックスに、「`key.snk`」と入力します。 **[キーファイルをパスワードで保護する]** チェック ボックスをオフにします。 Click **OK**.

6. TypeEquivalenceRuntime プロジェクトを右クリックし、 **[参照の追加]** をクリックします。 **[参照]** タブをクリックし、出力パスのフォルダーを参照します。 TypeEquivalenceInterface.dll ファイルを選択し、 **[OK]** をクリックします。

7. **ソリューション エクスプローラー**で、 **[参照]** フォルダーを展開します。 TypeEquivalenceInterface 参照を選択します。 TypeEquivalenceInterface 参照の [プロパティ] ウィンドウで、 **[特定バージョン]** プロパティを **[False]** に設定します。

8. SampleClass クラス ファイルに、SampleClass クラスを作成するための次のコードを追加します。

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using System.Text;
    using TypeEquivalenceInterface;

    namespace TypeEquivalenceRuntime
    {
        public class SampleClass : ISampleInterface
        {
            private string p_UserInput;
            public string UserInput { get { return p_UserInput; } }

            public void GetUserInput()
            {
                Console.WriteLine("Please enter a value:");
                p_UserInput = Console.ReadLine();
            }
        }
    }
    ```

9. プロジェクトを保存します。

10. TypeEquivalenceRuntime プロジェクトを右クリックし、 **[ビルド]** をクリックします。 クラス ライブラリの .dll ファイルがコンパイルされ、指定したビルド出力パス (たとえば、C:\TypeEquivalenceSample) に保存されます。

## <a name="creating-a-client-project"></a>クライアント プロジェクトの作成

#### <a name="to-create-the-type-equivalence-client-project"></a>型等価性クライアント プロジェクトを作成するには

1. Visual Studio で、 **[ファイル]** メニューの **[新規作成]** をポイントし、 **[プロジェクト]** をクリックします。

2. **[新しいプロジェクト]** ダイアログ ボックスの **[プロジェクトの種類]** ペインで、 **[Windows]** が選択されていることを確認します。 **[テンプレート]** ペインの **[コンソール アプリケーション]** を選択します。 **[名前]** ボックスに `TypeEquivalenceClient` と入力して、 **[OK]** をクリックします。 新しいプロジェクトが作成されます。

3. TypeEquivalenceClient プロジェクトを右クリックし、 **[プロパティ]** をクリックします。 **[ビルド]** タブをクリックします。出力パスを、TypeEquivalenceInterface プロジェクトで使用したのと同じ場所に設定します (たとえば、`C:\TypeEquivalenceSample`)。

4. TypeEquivalenceClient プロジェクトを右クリックし、 **[参照の追加]** をクリックします。 **[参照]** タブをクリックし、出力パスのフォルダーを参照します。 TypeEquivalenceInterface.dll ファイル (TypeEquivalenceRuntime.dll ではない) を選択し、 **[OK]** をクリックします。

5. **ソリューション エクスプローラー**で、 **[参照]** フォルダーを展開します。 TypeEquivalenceInterface 参照を選択します。 TypeEquivalenceInterface 参照の [プロパティ] ウィンドウで、 **[相互運用型の埋め込み]** プロパティを **[True]** に設定します。

6. Program.cs ファイルに、クライアント プログラムを作成するための次のコードを追加します。

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using System.Text;
    using TypeEquivalenceInterface;
    using System.Reflection;

    namespace TypeEquivalenceClient
    {
        class Program
        {
            static void Main(string[] args)
            {
                Assembly sampleAssembly = Assembly.Load("TypeEquivalenceRuntime");
                ISampleInterface sampleClass =
                    (ISampleInterface)sampleAssembly.CreateInstance("TypeEquivalenceRuntime.SampleClass");
                sampleClass.GetUserInput();
                Console.WriteLine(sampleClass.UserInput);
                Console.WriteLine(sampleAssembly.GetName().Version.ToString());
                Console.ReadLine();
            }
        }
    }
    ```

7. Ctrl キーを押しながら F5 キーを押して、プログラムをビルドおよび実行します。

## <a name="modifying-the-interface"></a>インターフェイスの変更

#### <a name="to-modify-the-interface"></a>インターフェイスを変更するには

1. Visual Studio で、 **[ファイル]** メニューの **[開く]** をポイントし、 **[プロジェクト/ソリューション]** をクリックします。

2. **[プロジェクトを開く]** ダイアログ ボックスで、TypeEquivalenceInterface プロジェクトを右クリックし、 **[プロパティ]** をクリックします。 **[アプリケーション]** タブをクリックします。 **[アセンブリ情報]** ボタンをクリックします。 **[アセンブリ バージョン]** と **[ファイル バージョン]** の値を `2.0.0.0` に変更します。

3. SampleInterface.cs ファイルを開きます。 ISampleInterface インターフェイスに、次のコード行を追加します。

    ```csharp
    DateTime GetDate();
    ```

    ファイルを保存します。

4. プロジェクトを保存します。

5. TypeEquivalenceInterface プロジェクトを右クリックし、 **[ビルド]** をクリックします。 クラス ライブラリ .dll ファイルの新バージョンがコンパイルされ、指定したビルド出力パス (たとえば、C:\TypeEquivalenceSample) に保存されます。

## <a name="modifying-the-runtime-class"></a>ランタイム クラスの変更

#### <a name="to-modify-the-runtime-class"></a>ランタイム クラスを変更するには

1. Visual Studio で、 **[ファイル]** メニューの **[開く]** をポイントし、 **[プロジェクト/ソリューション]** をクリックします。

2. **[プロジェクトを開く]** ダイアログ ボックスで、TypeEquivalenceRuntime プロジェクトを右クリックし、 **[プロパティ]** をクリックします。 **[アプリケーション]** タブをクリックします。 **[アセンブリ情報]** ボタンをクリックします。 **[アセンブリ バージョン]** と **[ファイル バージョン]** の値を `2.0.0.0` に変更します。

3. SampleClass.cs ファイルを開きます。 SampleClass クラスに次のコード行を追加します。

    ```csharp
    public DateTime GetDate()
    {
        return DateTime.Now;
    }
    ```

    ファイルを保存します。

4. プロジェクトを保存します。

5. TypeEquivalenceRuntime プロジェクトを右クリックし、 **[ビルド]** をクリックします。 クラス ライブラリ .dll ファイルの更新バージョンがコンパイルされ、前に指定したビルド出力パス (たとえば、C:\TypeEquivalenceSample) に保存されます。

6. ファイル エクスプローラーで、出力パスのフォルダー (たとえば、C:\TypeEquivalenceSample) を開きます。 TypeEquivalenceClient.exe をダブルクリックして、プログラムを実行します。 プログラムでは、再コンパイルを行わなくても、新バージョンの TypeEquivalenceRuntime アセンブリが反映されます。

## <a name="see-also"></a>関連項目

- [/link (C# コンパイラ オプション)](../../../language-reference/compiler-options/link-compiler-option.md)
- [C# プログラミング ガイド](../../index.md)
- [アセンブリを使用したプログラミング](../../../../framework/app-domains/programming-with-assemblies.md)
- [.NET のアセンブリ](../../../../standard/assembly/index.md)
