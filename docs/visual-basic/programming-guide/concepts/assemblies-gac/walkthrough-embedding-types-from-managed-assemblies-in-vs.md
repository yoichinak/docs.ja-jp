---
title: 'チュートリアル: Visual Studio でマネージド アセンブリからの型を埋め込む (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 56ed12ba-adff-4e9c-a668-7fcba80c4795
ms.openlocfilehash: 0c0de529a0005c9dbaf1f8d0f25957b217280e31
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67753024"
---
# <a name="walkthrough-embedding-types-from-managed-assemblies-in-visual-studio-visual-basic"></a>チュートリアル: Visual Studio でマネージド アセンブリからの型を埋め込む (Visual Basic)

厳密な名前を持つマネージド アセンブリから型情報を埋め込むと、アプリケーション内で型を疎結合して、バージョンに依存しないプログラムを実現できます。 つまり、各バージョン用の再コンパイルを必要とすることなく、マネージド ライブラリの複数のバージョンから型を使用するプログラムを記述できます。

型の埋め込みは、COM 相互運用と共によく使用されます (Microsoft Office からのオートメーション オブジェクトを使用するアプリケーションなど)。 型情報を埋め込むと、同じビルドのプログラムを、別のコンピューター上にある別バージョンの Microsoft Office と連携させることができます。 ただし、型の埋め込みはフル マネージド ソリューションと共に使用することもできます。

型情報は、次の特性を持つアセンブリから埋め込むことができます。

- アセンブリが、少なくとも 1 つのパブリック インターフェイスを公開している。

- 埋め込みインターフェイスに `ComImport` 属性と `Guid` 属性 (および一意の GUID) が付けられている。

- アセンブリに、`ImportedFromTypeLib` 属性または `PrimaryInteropAssembly` 属性、およびアセンブリ レベルの `Guid` 属性が付けられている。 (既定では、Visual Basic プロジェクト テンプレートに含めるアセンブリ レベル`Guid`属性)。

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

### <a name="to-create-the-type-equivalence-interface-project"></a>型等価性インターフェイス プロジェクトを作成するには

1. Visual Studio で、 **[ファイル]** メニューの **[新規作成]** をポイントし、 **[プロジェクト]** をクリックします。

2. **[新しいプロジェクト]** ダイアログ ボックスの **[プロジェクトの種類]** ペインで、 **[Windows]** が選択されていることを確認します。 **[テンプレート]** ペインで **[クラス ライブラリ]** を選択します。 **[名前]** ボックスに `TypeEquivalenceInterface` と入力して、 **[OK]** をクリックします。 新しいプロジェクトが作成されます。

3. **ソリューション エクスプ ローラー**Class1.vb ファイルを右クリックし、クリックして、**の名前を変更**します。 ファイルの名前を `ISampleInterface.vb` に変更し、Enter キーを押します。 ファイルの名前を変更すると、クラスの名前も `ISampleInterface` に変更されます。 このクラスは、クラスのパブリック インターフェイスを表します。

4. TypeEquivalenceInterface プロジェクトを右クリックし、 **[プロパティ]** をクリックします。 **[コンパイル]** タブをクリックします。開発用コンピューター上の有効な場所への出力パスを設定します (`C:\TypeEquivalenceSample` など)。 この場所は、このチュートリアルの後の手順でも使用されます。

5. プロジェクト プロパティの編集を続けたまま、 **[署名]** タブをクリックします。 **[アセンブリの署名]** オプションを選択します。 **[厳密な名前のキー ファイルを選択してください]** ボックスの一覧で **[<新規作成...>]** をクリックします。 **[キー ファイル名]** ボックスに、「`key.snk`」と入力します。 **[キーファイルをパスワードで保護する]** チェック ボックスをオフにします。 **[OK]** をクリックします。

6. ISampleInterface.vb ファイルを開きます。 ISampleInterface クラス ファイルに、ISampleInterface インターフェイスを作成するための次のコードを追加します。

    ```vb
    Imports System.Runtime.InteropServices

    <ComImport()>
    <Guid("8DA56996-A151-4136-B474-32784559F6DF")>
    Public Interface ISampleInterface
        Sub GetUserInput()
        ReadOnly Property UserInput As String
    End Interface
    ```

7. **[ツール]** メニューの **[GUID の作成]** をクリックします。 **[GUID の作成]** ダイアログ ボックスで、 **[レジストリ形式]** をクリックし、 **[コピー]** をクリックします。 **[終了]** をクリックします。

8. `Guid` 属性で、サンプルの GUID を削除し、 **[GUID の作成]** ダイアログ ボックスからコピーした GUID を貼り付けます。 コピーした GUID から中かっこ ({}) を削除します。

9. **[プロジェクト]** メニューの **[すべてのファイルを表示]** をクリックします。

10. **ソリューション エクスプ ローラー**、展開、 **My Project**フォルダー。 AssemblyInfo.vb をダブルクリックします。 ファイルに次の属性を追加します。

    ```vb
    <Assembly: ImportedFromTypeLib("")>
    ```

    ファイルを保存します。

11. プロジェクトを保存します。

12. TypeEquivalenceInterface プロジェクトを右クリックし、 **[ビルド]** をクリックします。 クラス ライブラリの .dll ファイルがコンパイルされ、指定したビルド出力パス (たとえば、C:\TypeEquivalenceSample) に保存されます。

## <a name="creating-a-runtime-class"></a>ランタイム クラスの作成

### <a name="to-create-the-type-equivalence-runtime-project"></a>型等価性ランタイム プロジェクトを作成するには

1. Visual Studio で、 **[ファイル]** メニューの **[新規作成]** をポイントし、 **[プロジェクト]** をクリックします。

2. **[新しいプロジェクト]** ダイアログ ボックスの **[プロジェクトの種類]** ペインで、 **[Windows]** が選択されていることを確認します。 **[テンプレート]** ペインで **[クラス ライブラリ]** を選択します。 **[名前]** ボックスに `TypeEquivalenceRuntime` と入力して、 **[OK]** をクリックします。 新しいプロジェクトが作成されます。

3. **ソリューション エクスプ ローラー**Class1.vb ファイルを右クリックし、クリックして、**の名前を変更**します。 ファイルの名前を `SampleClass.vb` に変更し、Enter キーを押します。 ファイルの名前を変更すると、クラスの名前も `SampleClass` に変更されます。 このクラスが `ISampleInterface` インターフェイスを実装します。

4. TypeEquivalenceRuntime プロジェクトを右クリックし、 **[プロパティ]** をクリックします。 **[コンパイル]** タブをクリックします。出力パスを、TypeEquivalenceInterface プロジェクトで使用したのと同じ場所に設定します (たとえば、`C:\TypeEquivalenceSample`)。

5. プロジェクト プロパティの編集を続けたまま、 **[署名]** タブをクリックします。 **[アセンブリの署名]** オプションを選択します。 **[厳密な名前のキー ファイルを選択してください]** ボックスの一覧で **[<新規作成...>]** をクリックします。 **[キー ファイル名]** ボックスに、「`key.snk`」と入力します。 **[キーファイルをパスワードで保護する]** チェック ボックスをオフにします。 **[OK]** をクリックします。

6. TypeEquivalenceRuntime プロジェクトを右クリックし、 **[参照の追加]** をクリックします。 **[参照]** タブをクリックし、出力パスのフォルダーを参照します。 TypeEquivalenceInterface.dll ファイルを選択し、 **[OK]** をクリックします。

7. **[プロジェクト]** メニューの **[すべてのファイルを表示]** をクリックします。

8. **ソリューション エクスプローラー**で、 **[参照]** フォルダーを展開します。 TypeEquivalenceInterface 参照を選択します。 TypeEquivalenceInterface 参照の [プロパティ] ウィンドウで、 **[特定バージョン]** プロパティを **[False]** に設定します。

9. SampleClass クラス ファイルに、SampleClass クラスを作成するための次のコードを追加します。

    ```vb
    Imports TypeEquivalenceInterface

    Public Class SampleClass
        Implements ISampleInterface

        Private p_UserInput As String
        Public ReadOnly Property UserInput() As String Implements ISampleInterface.UserInput
            Get
                Return p_UserInput
            End Get
        End Property

        Public Sub GetUserInput() Implements ISampleInterface.GetUserInput
            Console.WriteLine("Please enter a value:")
            p_UserInput = Console.ReadLine()
        End Sub
    End Class
    ```

10. プロジェクトを保存します。

11. TypeEquivalenceRuntime プロジェクトを右クリックし、 **[ビルド]** をクリックします。 クラス ライブラリの .dll ファイルがコンパイルされ、指定したビルド出力パス (たとえば、C:\TypeEquivalenceSample) に保存されます。

## <a name="creating-a-client-project"></a>クライアント プロジェクトの作成

### <a name="to-create-the-type-equivalence-client-project"></a>型等価性クライアント プロジェクトを作成するには

1. Visual Studio で、 **[ファイル]** メニューの **[新規作成]** をポイントし、 **[プロジェクト]** をクリックします。

2. **[新しいプロジェクト]** ダイアログ ボックスの **[プロジェクトの種類]** ペインで、 **[Windows]** が選択されていることを確認します。 **[テンプレート]** ペインの **[コンソール アプリケーション]** を選択します。 **[名前]** ボックスに `TypeEquivalenceClient` と入力して、 **[OK]** をクリックします。 新しいプロジェクトが作成されます。

3. TypeEquivalenceClient プロジェクトを右クリックし、 **[プロパティ]** をクリックします。 **[コンパイル]** タブをクリックします。出力パスを、TypeEquivalenceInterface プロジェクトで使用したのと同じ場所に設定します (たとえば、`C:\TypeEquivalenceSample`)。

4. TypeEquivalenceClient プロジェクトを右クリックし、 **[参照の追加]** をクリックします。 **[参照]** タブをクリックし、出力パスのフォルダーを参照します。 TypeEquivalenceInterface.dll ファイル (TypeEquivalenceRuntime.dll ではない) を選択し、 **[OK]** をクリックします。

5. **[プロジェクト]** メニューの **[すべてのファイルを表示]** をクリックします。

6. **ソリューション エクスプローラー**で、 **[参照]** フォルダーを展開します。 TypeEquivalenceInterface 参照を選択します。 TypeEquivalenceInterface 参照の [プロパティ] ウィンドウで、 **[相互運用型の埋め込み]** プロパティを **[True]** に設定します。

7. Module1.vb ファイルをクライアント プログラムを作成するには、次のコードを追加します。

    ```vb
    Imports TypeEquivalenceInterface
    Imports System.Reflection

    Module Module1

        Sub Main()
            Dim sampleAssembly = Assembly.Load("TypeEquivalenceRuntime")
            Dim sampleClass As ISampleInterface = CType( _
                sampleAssembly.CreateInstance("TypeEquivalenceRuntime.SampleClass"), ISampleInterface)
            sampleClass.GetUserInput()
            Console.WriteLine(sampleClass.UserInput)
            Console.WriteLine(sampleAssembly.GetName().Version)
            Console.ReadLine()
        End Sub

    End Module
    ```

8. Ctrl キーを押しながら F5 キーを押して、プログラムをビルドおよび実行します。

## <a name="modifying-the-interface"></a>インターフェイスの変更

### <a name="to-modify-the-interface"></a>インターフェイスを変更するには

1. Visual Studio で、 **[ファイル]** メニューの **[開く]** をポイントし、 **[プロジェクト/ソリューション]** をクリックします。

2. **[プロジェクトを開く]** ダイアログ ボックスで、TypeEquivalenceInterface プロジェクトを右クリックし、 **[プロパティ]** をクリックします。 **[アプリケーション]** タブをクリックします。 **[アセンブリ情報]** ボタンをクリックします。 **[アセンブリ バージョン]** と **[ファイル バージョン]** の値を `2.0.0.0` に変更します。

3. ISampleInterface.vb ファイルを開きます。 ISampleInterface インターフェイスに、次のコード行を追加します。

    ```vb
    Function GetDate() As Date
    ```

    ファイルを保存します。

4. プロジェクトを保存します。

5. TypeEquivalenceInterface プロジェクトを右クリックし、 **[ビルド]** をクリックします。 クラス ライブラリ .dll ファイルの新バージョンがコンパイルされ、指定したビルド出力パス (たとえば、C:\TypeEquivalenceSample) に保存されます。

## <a name="modifying-the-runtime-class"></a>ランタイム クラスの変更

### <a name="to-modify-the-runtime-class"></a>ランタイム クラスを変更するには

1. Visual Studio で、 **[ファイル]** メニューの **[開く]** をポイントし、 **[プロジェクト/ソリューション]** をクリックします。

2. **[プロジェクトを開く]** ダイアログ ボックスで、TypeEquivalenceRuntime プロジェクトを右クリックし、 **[プロパティ]** をクリックします。 **[アプリケーション]** タブをクリックします。 **[アセンブリ情報]** ボタンをクリックします。 **[アセンブリ バージョン]** と **[ファイル バージョン]** の値を `2.0.0.0` に変更します。

3. SampleClass.vb ファイルを開きます。 SampleClass クラスに次のコード行を追加します。

    ```vb
    Public Function GetDate() As DateTime Implements ISampleInterface.GetDate
        Return Now
    End Function
    ```

    ファイルを保存します。

4. プロジェクトを保存します。

5. TypeEquivalenceRuntime プロジェクトを右クリックし、 **[ビルド]** をクリックします。 クラス ライブラリ .dll ファイルの更新バージョンがコンパイルされ、前に指定したビルド出力パス (たとえば、C:\TypeEquivalenceSample) に保存されます。

6. ファイル エクスプローラーで、出力パスのフォルダー (たとえば、C:\TypeEquivalenceSample) を開きます。 TypeEquivalenceClient.exe をダブルクリックして、プログラムを実行します。 プログラムでは、再コンパイルを行わなくても、新バージョンの TypeEquivalenceRuntime アセンブリが反映されます。

## <a name="see-also"></a>関連項目

- [/link (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/link.md)
- [プログラミングの概念](../../../../visual-basic/programming-guide/concepts/index.md)
- [アセンブリを使用したプログラミング](../../../../framework/app-domains/programming-with-assemblies.md)
- [.NET のアセンブリ](../../../../standard/assembly/index.md)
