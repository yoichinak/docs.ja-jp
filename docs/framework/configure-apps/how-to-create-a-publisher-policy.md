---
title: '方法: 発行者ポリシーを作成する'
ms.date: 03/30/2017
helpviewer_keywords:
- publisher policy assembly
- publisher policy files
- GAC (global assembly cache), publisher policy assembly
- global assembly cache, publisher policy assembly
ms.assetid: 8046bc5d-2fa9-4277-8a5e-6dcc96c281d9
ms.openlocfilehash: ed73b9c15d5d9279b97063077f210d3ac5dc68e4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59227393"
---
# <a name="how-to-create-a-publisher-policy"></a>方法: 発行者ポリシーを作成する
アセンブリの販売できる状態の監視アプリケーションがアップグレード済みのアセンブリに発行者ポリシー ファイルを含めることによって、新しいバージョンのアセンブリを使用する必要があります。 発行者ポリシー ファイルは、アセンブリのリダイレクトとコードの基本設定を指定し、アプリケーション構成ファイルと同じ形式を使用します。 発行者ポリシー ファイルがアセンブリにコンパイルし、グローバル アセンブリ キャッシュに配置します。  
  
 パブリッシャー ポリシーを作成するのには、3 つの手順があります。  
  
1.  発行者ポリシー ファイルを作成します。  
  
2.  発行者ポリシー アセンブリを作成します。  
  
3.  発行者ポリシー アセンブリをグローバル アセンブリ キャッシュに追加します。  
  
 パブリッシャー ポリシー用のスキーマについては、「[アセンブリ バージョンのリダイレクト](../../../docs/framework/configure-apps/redirect-assembly-versions.md)します。 次の例は、パブリッシャー ポリシー ファイルの 1 つのバージョンをリダイレクトする`myAssembly`間。  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
       <dependentAssembly>  
         <assemblyIdentity name="myAssembly"  
                           publicKeyToken="32ab4ba45e0a69a1"  
                           culture="en-us" />  
         <!-- Redirecting to version 2.0.0.0 of the assembly. -->  
         <bindingRedirect oldVersion="1.0.0.0"  
                          newVersion="2.0.0.0"/>  
       </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 コード ベースを指定する方法については、次を参照してください。[アセンブリの場所を指定する](../../../docs/framework/configure-apps/specify-assembly-location.md)します。  
  
## <a name="creating-the-publisher-policy-assembly"></a>発行者ポリシー アセンブリを作成します。  
 使用して、[アセンブリ リンカー (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md)発行者ポリシー アセンブリを作成します。  
  
#### <a name="to-create-a-publisher-policy-assembly"></a>発行者ポリシー アセンブリを作成するには  
  
1.  コマンド プロンプトで次のコマンドを入力します。  
  
     **al /link:** *publisherPolicyFile* **/out:** *publisherPolicyAssemblyFile* **/keyfile:** *keyPairFile* **/platform:** *processorArchitecture*  
  
     このコマンドでは。  
  
    -   *PublisherPolicyFile*引数は、発行者ポリシー ファイルの名前です。  
  
    -   *PublisherPolicyAssemblyFile*引数は、このコマンドに起因する発行者ポリシー アセンブリの名前。 アセンブリ ファイルの名前は、形式に従う必要があります。  
  
         **ポリシー。** *majorNumber* **.** *minorNumber* **.** *mainAssemblyName* **.dll**  
  
    -   *KeyPairFile*引数はキー ペアを含むファイルの名前です。 アセンブリと同じキーのペアで発行者ポリシー アセンブリに署名する必要があります。  
  
    -   *ProcessorArchitecture*引数は、プロセッサ固有のアセンブリの対象となるプラットフォームを識別します。  
  
        > [!NOTE]
        >  特定のプロセッサ アーキテクチャを対象とする機能は、.NET Framework version 2.0 の新機能です。  
  
     次のコマンドと呼ばれる、発行者ポリシー アセンブリを作成する`policy.1.0.myAssembly`発行者ポリシー ファイルからと呼ばれる`pub.config`、内のキー ペアを使用して、アセンブリに厳密な名前を割り当てます、`sgKey.snk`ファイルを開き、アセンブリが、x86 を対象とするを指定します。プロセッサ アーキテクチャ。  
  
    ```  
    al /link:pub.config /out:policy.1.0.myAssembly.dll /keyfile:sgKey.snk /platform:x86  
    ```  
  
     発行者ポリシー アセンブリは、それが適用されるアセンブリのプロセッサ アーキテクチャと一致する必要があります。 したがって、アセンブリがある場合、<xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A>の値<xref:System.Reflection.ProcessorArchitecture.MSIL>でそのアセンブリの発行者ポリシー アセンブリを作成する必要があります`/platform:anycpu`します。 個別を提供する必要があります各プロセッサに固有のアセンブリの発行者ポリシー アセンブリ。  
  
     このルールの結果は、アセンブリのプロセッサ アーキテクチャを変更するには、バージョン番号のメジャーまたはマイナー コンポーネントを変更する必要がありますが正しいプロセッサ アーキテクチャを持つ新しい発行者ポリシー アセンブリを提供できるようにします。 古い発行者ポリシー アセンブリは、アセンブリが別のプロセッサ アーキテクチャを持つアセンブリをサービスことはできません。  
  
     もう 1 つの結果は、プロセッサ アーキテクチャを常に指定されているため、.NET Framework の以前のバージョンを使用してコンパイルされたアセンブリの発行者ポリシー アセンブリを作成するバージョン 2.0 のリンカーを使用することはできません。  
  
## <a name="adding-the-publisher-policy-assembly-to-the-global-assembly-cache"></a>発行者ポリシー アセンブリをグローバル アセンブリ キャッシュに追加します。  
 使用して、[グローバル アセンブリ キャッシュ ツール (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)発行者ポリシー アセンブリをグローバル アセンブリ キャッシュに追加します。  
  
#### <a name="to-add-the-publisher-policy-assembly-to-the-global-assembly-cache"></a>発行者ポリシー アセンブリをグローバル アセンブリ キャッシュに追加するには  
  
1.  コマンド プロンプトで次のコマンドを入力します。  
  
     **gacutil /i**  *publisherPolicyAssemblyFile*  
  
     次のコマンドは、追加`policy.1.0.myAssembly.dll`グローバル アセンブリ キャッシュにします。  
  
    ```  
    gacutil /i policy.1.0.myAssembly.dll  
    ```  
  
    > [!IMPORTANT]
    >  元の発行者ポリシー ファイルは、アセンブリと同じディレクトリにある場合を除き、発行者ポリシー アセンブリをグローバル アセンブリ キャッシュに追加できません。  
  
## <a name="see-also"></a>関連項目

- [アセンブリを使用したプログラミング](../../../docs/framework/app-domains/programming-with-assemblies.md)
- [ランタイムがアセンブリを検索する方法](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [構成ファイルを使用してアプリを構成する方法](../../../docs/framework/configure-apps/index.md)
- [ランタイム設定スキーマ](../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [構成ファイル スキーマ](../../../docs/framework/configure-apps/file-schema/index.md)
- [アセンブリ バージョンのリダイレクト](../../../docs/framework/configure-apps/redirect-assembly-versions.md)
