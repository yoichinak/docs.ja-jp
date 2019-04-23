---
title: '方法: 厳密な名前でアセンブリに署名する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- strong-named assemblies, signing with strong names
- signing assemblies
- assemblies [.NET Framework], signing
- assemblies [.NET Framework], strong-named
ms.assetid: 2c30799a-a826-46b4-a25d-c584027a6c67
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5580b6d8af7319397ad7eb6416941c2be0dcdb76
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59303434"
---
# <a name="how-to-sign-an-assembly-with-a-strong-name"></a>方法: 厳密な名前でアセンブリに署名する
厳密な名前でアセンブリに署名するには、いくつかの方法があります。  
  
-   Visual Studio でプロジェクトの **[プロパティ]** ダイアログ ボックスにある **[署名]** タブを使用する。 これは、厳密な名前でアセンブリに署名するための最も簡単で便利な方法です。  
  
-   [アセンブリ リンカー (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) を使用して、.NET Framework のコード モジュール (.netmodule ファイル) をキー ファイルにリンクする。  
  
-   アセンブリ属性を使用して、厳密な名前情報をコードに挿入する。 使用するキー ファイルが配置されている場所に応じて、 <xref:System.Reflection.AssemblyKeyFileAttribute> または <xref:System.Reflection.AssemblyKeyNameAttribute> 属性を使用できます。  
  
-   コンパイラ オプションを使用する。  
  
 厳密な名前でアセンブリに署名するには、暗号キー ペアが必要です。 キー ペアの作成の詳細については、「[方法:公開キーと秘密キーのキー ペアを作成する](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md)」を参照してください。  
  
### <a name="to-create-and-sign-an-assembly-with-a-strong-name-by-using-visual-studio"></a>Visual Studio を使用してアセンブリを作成し、厳密な名前でそのアセンブリに署名するには  
  
1. **ソリューション エクスプローラー**で、プロジェクトのショートカット メニューを開き、 **[プロパティ]** を選択します。  
  
2. **[署名]** タブを選択します。  
  
3. **[アセンブリの署名]** ボックスを選択します。  
  
4. **[厳密な名前のキー ファイルを選択してください]** ボックスで **[\<参照>]** をクリックし、キー ファイルに移動します。 新しいキー ファイルを作成するには、**[\<新規作成>]** を選択し、**[厳密な名前キーの作成]** ダイアログ ボックスでその名前を入力します。  
  
> [!NOTE]
>  [アセンブリの遅延署名](../../../docs/framework/app-domains/delay-sign-assembly.md)を行うには、公開キー ファイルを選択します。  
  
### <a name="to-create-and-sign-an-assembly-with-a-strong-name-by-using-the-assembly-linker"></a>アセンブリ リンカーを使用してアセンブリを作成し、厳密な名前でそのアセンブリに署名するには  
  
-   [Visual Studio 用開発者コマンド プロンプト](../../../docs/framework/tools/developer-command-prompt-for-vs.md)で次のコマンドを入力します。  
  
     **al** **/out:**\<*assemblyName*> *\<moduleName>* **/keyfile:**\<*keyfileName*>  
  
     それぞれの文字について以下に説明します。  
  
     *assemblyName*  
     アセンブリ リンカーが生成する、厳密な名前で署名されたアセンブリ (.dll ファイルまたは .exe ファイル) の名前。  
  
     *moduleName*  
     1 つ以上の型を含む、.NET Framework コード モジュール (.netmodule ファイル) の名前。 C# または Visual Basic で `/target:module` スイッチを使ってコードをコンパイルすることにより、.netmodule ファイルを作成できます。  
  
     *keyfileName*  
     キー ペアを格納しているコンテナーまたはファイルの名前。 アセンブリ リンカーは、関係の相対パスを現在のディレクトリとして解釈します。  
  
 次の例は、キー ファイル `MyAssembly.dll` を使用して厳密な名前でアセンブリ `sgKey.snk`に署名します。  
  
```  
al /out:MyAssembly.dll MyModule.netmodule /keyfile:sgKey.snk  
```  
  
 このツールの詳細については、「 [アセンブリ リカー](../../../docs/framework/tools/al-exe-assembly-linker.md)」を参照してください。  
  
#### <a name="to-sign-an-assembly-with-a-strong-name-by-using-attributes"></a>属性を使用して厳密な名前でアセンブリに署名するには  
  
1. <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=nameWithType> または <xref:System.Reflection.AssemblyKeyNameAttribute> 属性をソース コード ファイルに追加して、厳密な名前でアセンブリに署名するときに使用するキー ペアを格納するファイルまたはコンテナーの名前を指定します。  
  
2. ソース コード ファイルを通常どおりにコンパイルします。  
  
> [!NOTE]
>  C# および Visual Basic コンパイラは、ソース コードで <xref:System.Reflection.AssemblyKeyFileAttribute> または <xref:System.Reflection.AssemblyKeyNameAttribute> 属性が見つかった場合、コンパイラ警告を発行します (CS1699 と BC41008)。 この警告は無視してかまいません。  
  
 次の例は、 <xref:System.Reflection.AssemblyKeyFileAttribute> という名前のキー ファイルを指定して、 `keyfile.snk`属性を使用します。このキー ファイルは、アセンブリがコンパイルされるディレクトリにあります。  
  
 [!code-cpp[AssemblyName_KeyPair#21](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyName_KeyPair/CPP/keyfileattrib.cpp#21)]
 [!code-csharp[AssemblyName_KeyPair#21](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyName_KeyPair/CS/keyfileattrib.cs#21)]
 [!code-vb[AssemblyName_KeyPair#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyName_KeyPair/VB/keyfileattrib.vb#21)]  
  
 ソース ファイルのコンパイル時に、アセンブリに遅延署名することもできます。 詳細については、「 [アセンブリへの遅延署名](../../../docs/framework/app-domains/delay-sign-assembly.md)」を参照してください。  
  
### <a name="to-sign-an-assembly-with-a-strong-name-by-using-the-compiler"></a>コンパイラを使用して厳密な名前でアセンブリに署名するには  
  
-   C# と Visual Basic では `/keyfile` または `/delaysign` コンパイラ オプションを使用し、C++ では `/KEYFILE` または `/DELAYSIGN` リンカー オプションを使用して、ソース コード ファイルをコンパイルします。 オプション名の後に、コロンと、キー ファイルの名前を追加します。 コマンド ライン コンパイラを使用する場合は、ソース コード ファイルを格納するディレクトリにキー ファイルをコピーできます。  
  
     遅延署名については、「 [Delay Signing an Assembly](../../../docs/framework/app-domains/delay-sign-assembly.md)」を参照してください。  
  
     次の例は、C# コンパイラを使用し、アセンブリ `UtilityLibrary.dll` にキー ファイル `sgKey.snk` を使用して厳密な名前で署名します。  
  
    ```  
    csc /t:library UtilityLibrary.cs /keyfile:sgKey.snk  
    ```  
  
## <a name="see-also"></a>関連項目

- [厳密な名前付きアセンブリの作成と使用](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
- [方法: 公開キーと秘密キーのキー ペアを作成する](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md)
- [Al.exe (アセンブリ リンカー)](../../../docs/framework/tools/al-exe-assembly-linker.md)
- [アセンブリへの遅延署名](../../../docs/framework/app-domains/delay-sign-assembly.md)
- [アセンブリおよびマニフェストへの署名の管理](/visualstudio/ide/managing-assembly-and-manifest-signing)
- [[署名] ページ (プロジェクト デザイナー)](/visualstudio/ide/reference/signing-page-project-designer)
