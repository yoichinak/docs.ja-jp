---
title: -リンク (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- l compiler option [Visual Basic]
- EmbedInteropTypes
- embed interop types [COM Interop]
- -link compiler option [Visual Basic]
- /link compiler option [Visual Basic]
- link compiler option [Visual Basic]
- -l compiler option [Visual Basic]
- /l compiler option [Visual Basic]
ms.assetid: 1885f24a-86f5-486c-a064-9fb7e455ccec
ms.openlocfilehash: d8451a028def44ec7d5b629a1c0749321684e4d2
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/01/2019
ms.locfileid: "57202198"
---
# <a name="-link-visual-basic"></a>-リンク (Visual Basic)
指定したアセンブリ内の COM 型情報を、現在のコンパイル対象のプロジェクトで使用できるようにします。  
  
## <a name="syntax"></a>構文  
  
```  
-link:fileList  
' -or-  
-l:fileList  
```  
  
## <a name="arguments"></a>引数  
  
|用語|定義|  
|---|---|  
|`fileList`|必須。 アセンブリ ファイル名のコンマ区切りリスト。 ファイル名に空白が含まれている場合は、名前を二重引用符で囲みます。|  
  
## <a name="remarks"></a>Remarks  
 `-link` オプションを使用すると、埋め込み型情報を含むアプリケーションを配置できます。 その後、このアプリケーションは、埋め込み型情報を実装する、ランタイム アセンブリ内の型を使用できます。その際、ランタイム アセンブリへの参照は必要ありません。 ランタイム アセンブリのさまざまなバージョンが公開されている場合、埋め込み型情報を含むアプリケーションは、再コンパイルする必要なく、各種バージョンで動作できます。 例については、「[チュートリアル:マネージド アセンブリからの型の埋め込み](../../../visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md)」をご覧ください。  
  
 `-link` オプションの使用は、COM 相互運用を使用している場合に特に便利です。 COM 型を埋め込むことができるため、アプリケーションは、ターゲット コンピューター上にプライマリ相互運用機能アセンブリ (PIA) を必要としなくなります。 `-link` オプションを使用すると、コンパイラによって、COM 型情報は、参照先の相互運用アセンブリから結果としてコンパイルされるコードに埋め込まれます。 COM 型は、CLSID (GUID) 値によって識別されます。 その結果、同じ CLSID 値の同じ COM 型がインストールされているターゲット コンピューターでアプリケーションを実行できます。 Microsoft Office を自動化するアプリケーションが良い例です。 Office のようなアプリケーションは、通常、さまざまなバージョン間で同じ CLSID 値を保持するため、.NET Framework 4 以降がターゲット コンピューターにインストールされていて、参照先の COM 型に含まれているメソッド、プロパティ、またはイベントがアプリケーションで使用される限りは、そのアプリケーションで参照先の COM 型を使用できます。  
  
 `-link` オプションで埋め込まれるのは、インターフェイス、構造体、デリゲートのみです。 COM クラスの埋め込みはサポートされていません。  
  
> [!NOTE]
>  コードで埋め込み COM 型のインスタンスを作成する際は、適切なインターフェイスを使用してインスタンスを作成する必要があります。 コクラスを使用して埋め込み COM 型のインスタンスを作成しようとすると、エラーが発生します。  
  
 Visual Studio で `-link` オプションを設定するには、アセンブリ参照を追加し、`Embed Interop Types` プロパティを **true** に設定します。 `Embed Interop Types` プロパティの既定値は **false** です。  
  
 別の COM アセンブリ (アセンブリ B) を参照する COM アセンブリ (アセンブリ A) にリンクする場合、次のいずれかが当てはまるときは、アセンブリ B にもリンクする必要があります。  
  
-   アセンブリ A の型がアセンブリ B の型から継承されているか、アセンブリ B のインターフェイスを実装する。  
  
-   アセンブリ B の戻り値の型またはパラメーターの型を使用するフィールド、プロパティ、イベント、またはメソッドが呼び出される。  
  
 使用[-libpath](../../../visual-basic/reference/command-line-compiler/libpath.md)を 1 つ以上のアセンブリ参照があるディレクトリを指定します。  
  
 ように、 [/reference](../../../visual-basic/reference/command-line-compiler/reference.md)コンパイラ オプション、`-link`コンパイラ オプションの参照が頻繁に使用される、Vbc.rsp 応答ファイルを使用して[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]アセンブリ。 使用して、 [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)コンパイラ オプション、コンパイラが Vbc.rsp ファイルを使用したくない場合。  
  
 `-link` の省略形は `-l` です。  
  
## <a name="generics-and-embedded-types"></a>ジェネリック型と埋め込み型  
 以降のセクションでは、相互運用機能型を埋め込むアプリケーションでジェネリック型を使用する際の制限事項について説明します。  
  
### <a name="generic-interfaces"></a>ジェネリック インターフェイス  
 相互運用アセンブリから埋め込まれるジェネリック インターフェイスを使用することはできません。 これを次の例に示します。  
  
 [!code-vb[VbLinkCompiler#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/module1.vb#1)]  
  
### <a name="types-that-have-generic-parameters"></a>ジェネリック パラメーターを含む型  
 型が相互運用アセンブリから埋め込まれているジェネリック パラメーターを含む型は、外部アセンブリからの型である場合に使用できません。 この制限はインターフェイスには当てはまりません。 たとえば、<xref:Microsoft.Office.Interop.Excel> アセンブリで定義されている <xref:Microsoft.Office.Interop.Excel.Range> インターフェイスについて考えます。 ライブラリによって <xref:Microsoft.Office.Interop.Excel> アセンブリから相互運用型が埋め込まれ、型が <xref:Microsoft.Office.Interop.Excel.Range> インターフェイスであるパラメーターを含むジェネリック型を返すメソッドが公開される場合、次のコード例に示すように、そのメソッドはジェネリック インターフェイスを返す必要があります。  
  
 [!code-vb[VbLinkCompiler#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/utility.vb#2)]  
[!code-vb[VbLinkCompiler#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/utility.vb#3)]  
[!code-vb[VbLinkCompiler#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/utility.vb#4)]  
  
 次の例では、クライアント コードで、<xref:System.Collections.IList> ジェネリック インターフェイスを返すメソッドをエラーなしで呼び出すことができます。  
  
 [!code-vb[VbLinkCompiler#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/module1.vb#5)]  
  
## <a name="example"></a>例  
 次のコマンドラインは、ソース ファイルをコンパイル`OfficeApp.vb`からの参照アセンブリと`COMData1.dll`と`COMData2.dll`を生成する`OfficeApp.exe`します。  
  
```console  
vbc -link:COMData1.dll,COMData2.dll /out:OfficeApp.exe OfficeApp.vb  
```  
  
## <a name="see-also"></a>関連項目

- [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)
- [チュートリアル: マネージド アセンブリからの型の埋め込み](../../../visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md)
- [-参照 (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
- [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [-libpath](../../../visual-basic/reference/command-line-compiler/libpath.md)
- [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [COM 相互運用の概要](../../../visual-basic/programming-guide/com-interop/introduction-to-com-interop.md)
