---
title: <loadFromRemoteSources> 要素
ms.date: 05/24/2018
helpviewer_keywords:
- loadFromRemoteSources element
- <loadFromRemoteSources> element
ms.assetid: 006d1280-2ac3-4db6-a984-a3d4e275046a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7568129f30267b212737ec8aa688cf882e19bbff
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704597"
---
# <a name="loadfromremotesources-element"></a>\<loadFromRemoteSources > 要素
リモート ソースから読み込まれたアセンブリに対して、.NET Framework 4 以降の完全な信頼を付与するかどうかを指定します。
  
> [!NOTE]
>  場合は、Visual Studio プロジェクトのエラー一覧またはビルド エラーのエラー メッセージのため、この記事にダイレクトされたを参照してください。[方法。Visual Studio で Web からアセンブリを使用して](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ee890038(v=vs.100))します。  
  
 \<configuration>  
\<runtime>  
\<loadFromRemoteSources>  
  
## <a name="syntax"></a>構文  
  
```xml  
<loadFromRemoteSources    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>属性と要素
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`enabled`|必須の属性です。<br /><br /> リモート ソースから読み込まれたアセンブリに対して、完全な信頼を付与する必要があるかどうかを指定します。|  
  
## <a name="enabled-attribute"></a>enabled 属性  
  
|[値]|説明|  
|-----------|-----------------|  
|`false`|リモート ソースからアプリケーションに完全な信頼を付与しないでください。 既定値です。|  
|`true`|リモート ソースからアプリケーションへの完全な信頼を付与します。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|ランタイム初期化オプションに関する情報を含んでいます。|  
  
## <a name="remarks"></a>Remarks

.NET Framework 3.5 以前のバージョンで、リモートの場所からアセンブリを読み込む場合に、アセンブリ内のコードを読み込み元のゾーンに依存している許可セットで部分信頼で実行されます。 たとえば、web サイトからアセンブリをロードする場合インターネット ゾーンに読み込まれ、インターネット アクセス許可のセットを許可は。 つまり、インターネットのサンド ボックス内で実行します。

以降、.NET Framework 4 では、コード アクセス セキュリティ (CAS) ポリシーが無効になり、アセンブリが完全信頼で読み込まれます。 読み込まれたアセンブリに完全な信頼を付与これは通常、<xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>サンド ボックス化された以前されていたメソッド。 これを防ぐためには、リモート ソースから読み込まれるアセンブリでコードを実行する機能は既定で無効になります。 リモートのアセンブリを読み込もうとした場合、既定で、<xref:System.IO.FileLoadException>次がスローされるように、例外メッセージ。

```text
System.IO.FileNotFoundException: Could not load file or assembly 'file:assem.dll' or one of its dependencies. Operation is not supported. 
(Exception from HRESULT: 0x80131515)
File name: 'file:assem.dll' ---> 
System.NotSupportedException: An attempt was made to load an assembly from a network location which would have caused the assembly 
to be sandboxed in previous versions of the .NET Framework. This release of the .NET Framework does not enable CAS policy by default, 
so this load may be dangerous. If this load is not intended to sandbox the assembly, please enable the loadFromRemoteSources switch. 
```

アセンブリを読み込むし、そのコードを実行、する必要がありますか。

- アセンブリのサンド ボックスを明示的に作成 (を参照してください[方法。サンド ボックスで部分信頼コードを実行](../../../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md))。

- 完全信頼でアセンブリのコードを実行します。 構成することで、これを行う、`<loadFromRemoteSources>`要素。 .NET Framework の以前のバージョンで部分信頼で実行するアセンブリが .NET Framework 4 およびそれ以降のバージョンで完全な信頼で実行されるように指定できます。

> [!IMPORTANT]
> アセンブリが完全信頼で実行されない場合は、この構成要素を設定しないでください。 代わりに、作成、セキュリティで保護された<xref:System.AppDomain>アセンブリの読み込み先となります。

`enabled`属性、`<loadFromRemoteSources>`要素は、コード アクセス セキュリティ (CAS) を無効にした場合にのみ有効です。 既定では、.NET Framework 4 およびそれ以降のバージョンの CAS ポリシーが無効になります。 設定した場合`enabled`に`true`、リモートのアセンブリに完全な信頼が与えられます。

場合`enabled`に設定されていない`true`、<xref:System.IO.FileLoadException>次の条件のいずれかでスローされます。

- 現在のドメインのサンド ボックス化動作は、.NET Framework 3.5 では、その動作からは異なります。 これは、CAS ポリシーを無効にして、現在のドメインがサンド ボックス化が必要です。

- 読み込まれるアセンブリでない、`MyComputer`ゾーン。

設定、`<loadFromRemoteSources>`要素`true`によりこの例外がスローされます。 これにより、ことをせず、サンド ボックスに、共通言語ランタイムのセキュリティを読み込まれたアセンブリを指定してで実行を許可することができます完全な信頼。

## <a name="notes"></a>メモ

- .NET Framework 4.5 以降のバージョンで、アセンブリをローカル ネットワーク共有に完全信頼で実行既定では有効にする必要はありません、`<loadFromRemoteSources>`要素。

- アプリケーションが web サイトからコピーされた場合としてマークされている Windows で web アプリケーションでは、ローカル コンピューター上にある場合でもです。 その指定を変更するには、ファイルのプロパティを変更することで、または使用することができます、`<loadFromRemoteSources>`完全信頼のアセンブリに与える要素。 代わりに、使用することができます、<xref:System.Reflection.Assembly.UnsafeLoadFrom%2A>オペレーティング システムは、web から読み込まれたものとしてフラグが設定されるローカル アセンブリを読み込みます。

- 取得することがあります、 <xref:System.IO.FileLoadException> Windows Virtual PC アプリケーションで実行されているアプリケーションでします。 これは、ホスト コンピュータ上のリンクされたフォルダーからファイルをロードしようとするときに発生します。 経由でリンクされているフォルダーからファイルをロードしようとするときに起こる可能性も[Remote Desktop Services](https://go.microsoft.com/fwlink/?LinkId=182775) (Terminal Services)。 例外を避けるためには、次のように設定します。`enabled`に`true`します。

## <a name="configuration-file"></a>構成ファイル

この要素では、通常は、アプリケーション構成ファイルで使用しますが、コンテキストに応じて他の構成ファイルで使用できます。 詳細については、この記事を参照してください。[詳細暗黙的な使用の CAS ポリシー: loadFromRemoteSources](https://go.microsoft.com/fwlink/p/?LinkId=266839) .NET セキュリティ ブログにします。  

## <a name="example"></a>例

次の例では、リモート ソースから読み込まれたアセンブリに完全な信頼を付与する方法を示します。

```xml
<configuration>  
   <runtime>  
      <loadFromRemoteSources enabled="true"/>  
   </runtime>  
</configuration>  
```

## <a name="see-also"></a>関連項目

- [CAS ポリシーの暗黙的な複数の使用: loadFromRemoteSources](https://go.microsoft.com/fwlink/p/?LinkId=266839)
- [方法: サンドボックスで部分信頼コードを実行する](../../../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)
- [ランタイム設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)
- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>
