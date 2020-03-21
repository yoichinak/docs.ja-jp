---
title: <loadFromRemoteSources> 要素
ms.date: 05/24/2018
helpviewer_keywords:
- loadFromRemoteSources element
- <loadFromRemoteSources> element
ms.assetid: 006d1280-2ac3-4db6-a984-a3d4e275046a
ms.openlocfilehash: a0dcffe378cdd09de0fbd8f0a6ef0635c033fd9c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154063"
---
# <a name="loadfromremotesources-element"></a>\<要素>リモートソースを読み込む
リモート ソースから読み込まれたアセンブリに .NET Framework 4 以降で完全な信頼を付与するかどうかを指定します。
  
> [!NOTE]
> Visual Studio プロジェクトのエラー一覧のエラー メッセージまたはビルド エラーが原因でこの資料に指示された場合は、「[方法 : Visual Studio で Web からアセンブリを使用する](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ee890038(v=vs.100))」を参照してください。  
  
[**\<構成>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<ランタイム>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<>からリモートソースを読み込む**  
  
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
|`enabled`|必須の属性です。<br /><br /> リモート ソースから読み込まれるアセンブリに完全信頼を付与するかどうかを指定します。|  
  
## <a name="enabled-attribute"></a>有効な属性  
  
|Value|説明|  
|-----------|-----------------|  
|`false`|リモート ソースからのアプリケーションに完全な信頼を付与しないでください。 これは既定値です。|  
|`true`|リモート ソースからのアプリケーションに完全な信頼を付与します。|  
  
### <a name="child-elements"></a>子要素  
 [なし] :  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|ランタイム初期化オプションに関する情報を含んでいます。|  
  
## <a name="remarks"></a>解説

.NET Framework 3.5 以前のバージョンでは、リモートの場所からアセンブリを読み込むと、アセンブリ内のコードは、アセンブリの読み込み元のゾーンに依存する許可セットを使用して部分的に信頼されて実行されます。 たとえば、Web サイトからアセンブリを読み込むと、そのアセンブリはインターネット ゾーンに読み込まれ、インターネット アクセス許可セットが付与されます。 つまり、インターネットサンドボックスで実行されます。

.NET Framework 4 以降、コード アクセス セキュリティ (CAS) ポリシーは無効になり、アセンブリは完全信頼で読み込まれます。 通常、これは以前にサンドボックス化されていたメソッドを読み込んだアセンブリに<xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>完全な信頼を与えます。 これを防ぐために、リモート ソースから読み込まれたアセンブリでコードを実行する機能は、既定で無効になっています。 既定では、リモート アセンブリを読み込もうとすると<xref:System.IO.FileLoadException>、次のような例外メッセージがスローされます。

```text
System.IO.FileNotFoundException: Could not load file or assembly 'file:assem.dll' or one of its dependencies. Operation is not supported.
(Exception from HRESULT: 0x80131515)
File name: 'file:assem.dll' --->
System.NotSupportedException: An attempt was made to load an assembly from a network location which would have caused the assembly
to be sandboxed in previous versions of the .NET Framework. This release of the .NET Framework does not enable CAS policy by default,
so this load may be dangerous. If this load is not intended to sandbox the assembly, please enable the loadFromRemoteSources switch.
```

アセンブリを読み込んでそのコードを実行するには、次のいずれかを実行する必要があります。

- アセンブリのサンドボックスを明示的に作成します (「[方法 : サンドボックスで部分的に信頼されたコードを実行](../../../misc/how-to-run-partially-trusted-code-in-a-sandbox.md)する」を参照)。

- アセンブリのコードを完全信頼で実行します。 これは`<loadFromRemoteSources>`、要素を構成することによって行います。 このクラスでは、以前のバージョンの .NET Framework で部分信頼で実行されるアセンブリが 、.NET Framework 4 以降のバージョンで完全に信頼されたバージョンで実行されるように指定できます。

> [!IMPORTANT]
> アセンブリが完全信頼で実行されない場合は、この構成要素を設定しないでください。 代わりに、アセンブリを読<xref:System.AppDomain>み込むサンドボックスを作成します。

要素`enabled`の`<loadFromRemoteSources>`属性は、コード アクセス セキュリティ (CAS) が無効になっている場合にのみ有効です。 既定では、CAS ポリシーは .NET Framework 4 以降のバージョンでは無効になっています。 に`enabled``true`設定すると、リモート アセンブリには完全な信頼が与えられます。

に`enabled`設定`true`されていない場合、a<xref:System.IO.FileLoadException>は次のいずれかの条件でスローされます。

- 現在のドメインのサンドボックスの動作は、.NET Framework 3.5 での動作とは異なります。 これには、CAS ポリシーを無効にし、現在のドメインをサンドボックス化しない必要があります。

- 読み込まれるアセンブリが`MyComputer`ゾーンから取得されていません。

この例外`<loadFromRemoteSources>`がスロー`true`されないように要素を設定します。 これにより、共通言語ランタイムを使用して、読み込まれたアセンブリをセキュリティでサンドボックス化することや、完全信頼で実行できることを指定できます。

## <a name="notes"></a>Notes

- .NET Framework 4.5 以降のバージョンでは、ローカル ネットワーク上のアセンブリは既定で完全な信頼で実行されます。要素を有効にする`<loadFromRemoteSources>`必要はありません。

- Web からコピーされたアプリケーションは、ローカル コンピューターに存在する場合でも、Web アプリケーションとして Windows によってフラグが設定されます。 ファイル プロパティを変更して指定を変更するか、要素を`<loadFromRemoteSources>`使用してアセンブリに完全な信頼を付与できます。 代わりに、<xref:System.Reflection.Assembly.UnsafeLoadFrom%2A>このメソッドを使用して、オペレーティング システムが Web から読み込まれたとフラグを立てたローカル アセンブリを読み込むことができます。

- Windows Virtual <xref:System.IO.FileLoadException> PC アプリケーションで実行されているアプリケーションで を取得できます。 これは、ホスト コンピューター上のリンクされたフォルダーからファイルを読み込もうとしたときに発生する可能性があります。 また、[リモート デスクトップ サービス](/windows/win32/termserv/terminal-services-portal)(ターミナル サービス) を介してリンクされたフォルダからファイルを読み込もうとしたときにも発生することがあります。 この例外を回避するには、 `enabled` `true`に設定します。

## <a name="configuration-file"></a>構成ファイル

この要素は、通常、アプリケーション構成ファイルで使用されますが、コンテキストに応じて他の構成ファイルで使用できます。 詳細については、.NET セキュリティブログの記事[「CAS ポリシーの暗黙的な使用: loadFromRemoteSources」](https://docs.microsoft.com/archive/blogs/shawnfa/more-implicit-uses-of-cas-policy-loadfromremotesources)を参照してください。  

## <a name="example"></a>例

リモート ソースから読み込まれたアセンブリに完全な信頼を付与する方法を次の例に示します。

```xml
<configuration>  
   <runtime>  
      <loadFromRemoteSources enabled="true"/>  
   </runtime>  
</configuration>  
```

## <a name="see-also"></a>関連項目

- [CAS ポリシーのより暗黙的な使用: 読み込みリモート ソース](https://docs.microsoft.com/archive/blogs/shawnfa/more-implicit-uses-of-cas-policy-loadfromremotesources)
- [方法 : サンドボックスで部分信頼コードを実行する](../../../misc/how-to-run-partially-trusted-code-in-a-sandbox.md)
- [ランタイム設定スキーマ](index.md)
- [構成ファイル スキーマ](../index.md)
- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>
