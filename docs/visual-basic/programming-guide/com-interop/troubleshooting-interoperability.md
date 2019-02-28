---
title: 相互運用性のトラブルシューティング (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- interop, deploying assemblies
- assemblies [Visual Basic]
- interop, installing assemblies that share components
- COM objects, troubleshooting
- interop, sharing components
- troubleshooting interoperability [Visual Basic]
- interoperability, troubleshooting
- COM interop [Visual Basic], troubleshooting
- assemblies [Visual Basic], deploying
- troubleshooting Visual Basic, interoperability
- interop assemblies
- interoperability, sharing components
- shared components, using with assemblies
ms.assetid: b324cc1e-b03c-4f39-aea6-6a6d5bfd0e37
ms.openlocfilehash: dc5262d62d32ad3f79c4f4e2c4d9f862dbce3727
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56976890"
---
# <a name="troubleshooting-interoperability-visual-basic"></a>相互運用性のトラブルシューティング (Visual Basic)
マネージ コードと COM の相互運用するときに、 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]、1 つ以上の次の一般的な問題が発生する可能性があります。  
  
##  <a name="vbconinteroperabilitymarshalinganchor1"></a> 相互運用マーシャ リング  
 データ型でないを使用する必要がありますの一部、[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]します。 相互運用機能アセンブリ、COM オブジェクトの作業のほとんどを処理するが、マネージ オブジェクトが COM に公開するときに使用されるデータ型を制御する必要があります。 たとえば、クラス ライブラリ内の構造体を指定する必要があります、`BStr`アンマネージド型 Visual Basic 6.0 と以前のバージョンで作成された COM オブジェクトに送信される文字列。 このような場合は、使用することができます、<xref:System.Runtime.InteropServices.MarshalAsAttribute>がアンマネージ型として公開するマネージ型の属性。  
  
##  <a name="vbconinteroperabilitymarshalinganchor2"></a> アンマネージ コードへの固定長文字列のエクスポート  
 Visual Basic 6.0 と以前のバージョンでは、文字列は、終端の null 文字を使用せずにバイトのシーケンスとして COM オブジェクトにエクスポートされます。 他の言語と互換性のため、Visual Basic .NET には、文字列をエクスポートするときに終端文字が含まれます。 この非互換性に対処する最善の方法は、文字列の配列として、終了文字がないをエクスポートする`Byte`または`Char`します。  
  
##  <a name="vbconinteroperabilitymarshalinganchor3"></a> 継承階層のエクスポート  
 マネージ クラスが COM オブジェクトとして公開されている場合に階層が平坦化します。 たとえば、メンバーを持つ基本クラスを定義して、COM オブジェクトとして公開されている派生クラスで基底クラスを継承し、COM オブジェクトで、派生クラスを使用するクライアントは継承されたメンバーを使用できません。 基本クラスのメンバーは、基底クラスのインスタンスとしてのみ COM オブジェクトからアクセスでき、基本クラスが COM オブジェクトとしても作成する場合にのみです。  
  
## <a name="overloaded-methods"></a>オーバーロードされたメソッド  
 COM でサポートされていませんが、Visual Basic では、オーバー ロードされたメソッドを作成できますが、 オーバー ロードされたメソッドを含むクラスは、COM オブジェクトとして公開される、ときに、新しいメソッドの名前は、オーバー ロードされたメソッドに対して生成されます。  
  
 たとえばの 2 つのオーバー ロードを持つクラスである、`Synch`メソッド。 クラスは、COM オブジェクトとして公開される、ときに新規生成されたメソッド名になります`Synch`と`Synch_2`します。  
  
 名前を変更すると、COM オブジェクトのコンシューマーを 2 つの問題が発生できます。  
  
1.  クライアントでは、生成されたメソッド名は予期しない可能性があります。  
  
2.  新しいオーバー ロードがクラスまたはその基本クラスに追加されたときに、COM オブジェクトとして公開されているクラスで生成されたメソッド名を変更できます。 バージョン管理の問題がある可能性があります。  
  
 両方の問題を解決するために各メソッドに、COM オブジェクトとして公開されるオブジェクトを開発するときに、オーバー ロードを使用する代わりに、一意の名前を指定します。  
  
##  <a name="vbconinteroperabilitymarshalinganchor4"></a> 相互運用機能アセンブリを介して COM オブジェクトの使用  
 表す COM オブジェクトの置き換えをマネージ コードが表示される場合とほとんど同じように、相互運用機能アセンブリを使用します。 ただし、これらは、ラッパーと実際の COM オブジェクトであるためには、相互運用機能アセンブリと標準のアセンブリを使用して違いです。 相違点には、クラス、およびパラメーターと戻り値のデータ型の公開が含まれます。  
  
##  <a name="vbconinteroperabilitymarshalinganchor5"></a> 両方のインターフェイスとして公開されるクラスとクラス  
 標準のアセンブリ、クラスとは異なり、COM クラスは、COM クラスを表すクラスとインターフェイスの両方と相互運用機能アセンブリで公開されます。 インターフェイスの名前は、COM クラスのと同じです。 相互運用機能のクラスの名前は、元の COM クラスのと同じですが、「クラス」を追加、word とします。 たとえば、COM オブジェクトの相互運用機能アセンブリへの参照を使用して、プロジェクトがあるとします。 COM クラスの名前は場合`MyComClass`、IntelliSense やオブジェクト ブラウザーには、という名前のインターフェイスを表示する`MyComClass`という名前のクラスと`MyComClassClass`します。  
  
##  <a name="vbconinteroperabilitymarshalinganchor6"></a> .NET Framework クラスのインスタンスを作成します。  
 通常のインスタンスを作成する、[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]クラスを使用して、`New`クラス名を含むステートメント。 相互運用機能アセンブリによって表される COM クラスは、1 つのケースを使用することができます、`New`ステートメント インターフェイスを使用します。 使用して、COM クラスを使用している場合を除き、`Inherits`ステートメントでは、クラスと同様に、インターフェイスを使用することができます。 次のコードを作成する方法を示します、 `Command` Microsoft ActiveX データ オブジェクト 2.8 ライブラリ COM オブジェクトへの参照があるプロジェクト内のオブジェクト。  
  
 [!code-vb[VbVbalrInterop#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#20)]  
  
 ただし、派生クラスのベースとして COM クラスを使用する場合は、次のコードのように、COM クラスを表す相互運用機能クラスを使用する必要があります。  
  
 [!code-vb[VbVbalrInterop#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#21)]  
  
> [!NOTE]
>  相互運用機能アセンブリは、COM クラスを表すインターフェイスを暗黙的に実装します。 使用してください、`Implements`これらのインターフェイスまたはエラーを実装するステートメントになります。  
  
##  <a name="vbconinteroperabilitymarshalinganchor7"></a> パラメーターと戻り値のデータ型  
 相互運用機能アセンブリのメンバーは、標準のアセンブリのメンバーとは異なりの元のオブジェクトの宣言で使用されるものとは異なるデータ型があります。 相互運用機能アセンブリは COM 型を互換性のある共通言語ランタイムの型に暗黙的に変換しますが、両方の側で実行時エラーを防ぐために使用されるデータ型に注意する必要があります。 たとえば、Visual Basic 6.0 以前のバージョンでは、型の値で作成された COM オブジェクトで`Integer`前提としています、[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]同等の型、`Short`します。 使用する前に、インポートされたメンバーの特性を調べるオブジェクト ブラウザーを使用することをお勧めします。  
  
##  <a name="vbconinteroperabilitymarshalinganchor8"></a> モジュール レベルの COM メソッド  
 ほとんどの COM オブジェクトを使用して COM クラスのインスタンスを作成して使用、`New`キーワードと、オブジェクトのメソッドを呼び出しています。 このルールの 1 つの例外は、COM オブジェクトが含まれている`AppObj`または`GlobalMultiUse`COM クラス。 このようなクラスには、Visual Basic .NET のクラスで、モジュール レベル メソッドに似ています。 Visual Basic 6.0 と以前のバージョンを暗黙的に作成のようなオブジェクトのインスタンスが初めてのメソッドのいずれかを呼び出します。 たとえば、Visual Basic 6.0 で追加できます 3.6 DAO オブジェクト ライブラリの呼び出しへの参照、`DBEngine`インスタンスを作成しなくてもメソッド。  
  
```vb  
Dim db As DAO.Database  
' Open the database.  
Set db = DBEngine.OpenDatabase("C:\nwind.mdb")  
' Use the database object.  
```  
  
 Visual Basic .NET では、それらのメソッドを使用する前に常に COM オブジェクトのインスタンスを作成することが必要です。 Visual Basic でこれらのメソッドを使用するには、目的のクラスの変数を宣言し、新しいキーワードを使用して、オブジェクト変数にオブジェクトを割り当てます。 `Shared`ことを確認する場合に、キーワードを使用できるクラスの 1 つのインスタンスが作成されます。  
  
 [!code-vb[VbVbalrInterop#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#23)]  
  
##  <a name="vbconinteroperabilitymarshalinganchor9"></a> イベント ハンドラーに未処理のエラー  
 1 つの一般的な相互運用機能の問題には、COM オブジェクトによって生成されるイベントを処理するイベント ハンドラーでエラーが含まれます。 具体的を使用してエラーをチェックする場合を除き、このようなエラーは無視されます`On Error`または`Try...Catch...Finally`ステートメント。 たとえば、次の例は、Microsoft ActiveX データ オブジェクト 2.8 ライブラリ COM オブジェクトへの参照を含む Visual Basic .NET プロジェクトです。  
  
 [!code-vb[VbVbalrInterop#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#24)]  
  
 この例では、想定どおりにエラーが発生します。 ただし、せず同じ例では、しようとすると、`Try...Catch...Finally`使用する場合と同様、ブロック、エラーは無視されます、`OnError Resume Next`ステートメント。 エラー処理、ゼロによる除算はサイレント モードで失敗します。 このようなエラーは、ハンドルされない例外エラーを発生させることはありません、ためには、COM オブジェクトからイベントを処理するイベント ハンドラーで例外処理のいくつかの形式を使用することが重要です。  
  
### <a name="understanding-com-interop-errors"></a>COM 相互運用機能の問題を理解します。  
 エラー処理、相互運用呼び出しは多くの場合、ほとんどの情報を提供するエラーを生成します。 可能であれば、構造化エラーが発生したときに、問題に関する詳細情報を提供する処理を使用します。 アプリケーションをデバッグする場合は特に便利にできます。 例:  
  
 [!code-vb[VbVbalrInterop#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#25)]  
  
 例外オブジェクトの内容を調べることで、エラーの説明、HRESULT を COM エラーのソースなどの情報を確認できます。  
  
##  <a name="vbconinteroperabilitymarshalinganchor10"></a> ActiveX コントロールに関する問題  
 問題が発生せずに、Visual Basic 6.0 で動作するほとんどの ActiveX コントロールが Visual Basic .NET で作業します。 コンテナー コントロール、またはその他のコントロールを視覚的に格納しているコントロールは、主な例外があります。 Visual Studio で正しく動作しない以前のコントロールのいくつかの例は次のとおりです。  
  
-   Microsoft Forms 2.0 フレーム コントロール  
  
-   アップダウン コントロール、スピン コントロールとも呼ばれます  
  
-   Sheridan タブ コントロール  
  
 サポートされていない ActiveX コントロールの問題のみのいくつか回避策があります。 元のソース コードを所有している場合は、既存のコントロールを Visual Studio に移行できます。 それ以外の場合、更新、ソフトウェア ベンダーに確認できます。NET と互換性のあるバージョン コントロールに置き換えるのでは、ActiveX コントロールがサポートされていません。  
  
##  <a name="vbconinteroperabilitymarshalinganchor11"></a> コントロールの ByRef の読み取り専用プロパティの引き渡し  
 Visual Basic .NET は、渡すときに場合があります"エラー 0x800A017F CTL_E_SETNOTSUPPORTED"などの COM エラーを生成`ReadOnly`プロパティとして、一部の古い ActiveX コントロールの`ByRef`他のプロシージャのパラメーター。 Visual Basic 6.0 からプロシージャの呼び出しでは、エラーは発生せず、パラメーターとして扱われます値で渡すと同様です。 Visual Basic .NET のエラー メッセージでは、プロパティがないプロパティを変更しようとしていることを示します`Set`プロシージャ。  
  
 呼び出されるプロシージャにアクセスする場合を使用してこのエラーを防ぐことができます、`ByVal`を受け取るパラメーターを宣言するキーワード`ReadOnly`プロパティ。 例:  
  
 [!code-vb[VbVbalrInterop#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#26)]  
  
 呼び出されるプロシージャのソース コードへのアクセスがない、値によって、余分な呼び出し元のプロシージャの周囲に角かっこのセットを追加することで渡されるプロパティを強制することができます。 たとえば、プロジェクトでは、Microsoft ActiveX データ オブジェクト 2.8 ライブラリ COM オブジェクトへの参照を含む、次のように使用します。  
  
 [!code-vb[VbVbalrInterop#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#27)]  
  
##  <a name="vbconinteroperabilitymarshalinganchor12"></a> 相互運用機能を公開するアセンブリの配置  
 COM インターフェイスを公開するアセンブリの展開固有の課題を表示します。 たとえば、潜在的な問題は、別のアプリケーションが同じ COM アセンブリを参照するときに発生します。 別のアプリケーションがまだ以前のバージョンのアセンブリを使用して新しいバージョンのアセンブリをインストールすると、このような状況が一般的です。 DLL を共有するアセンブリをアンインストールする場合行うことができます意図せずに使用できない他のアセンブリ。  
  
 この問題を回避するには、共有アセンブリをグローバル アセンブリ キャッシュ (GAC) にインストールをコンポーネントのマージ モジュールを使用する必要があります。 GAC にアプリケーションをインストールできない場合は、これでバージョン固有のサブディレクトリに CommonFilesFolder にインストールしてください。  
  
 共有されていないアセンブリは、呼び出し元のアプリケーションでのディレクトリに並べて配置してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [COM 相互運用](../../../visual-basic/programming-guide/com-interop/index.md)
- [Tlbimp.exe (タイプ ライブラリ インポーター)](../../../framework/tools/tlbimp-exe-type-library-importer.md)
- [Tlbexp.exe (タイプ ライブラリ エクスポーター)](../../../framework/tools/tlbexp-exe-type-library-exporter.md)
- [チュートリアル: COM オブジェクトによる継承の実装](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)
- [Inherits ステートメント](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [グローバル アセンブリ キャッシュ](../../../framework/app-domains/gac.md)
