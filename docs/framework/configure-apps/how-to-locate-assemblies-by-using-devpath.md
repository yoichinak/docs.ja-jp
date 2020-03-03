---
title: '方法: DEVPATH を使用してアセンブリを指定する'
ms.date: 03/30/2017
helpviewer_keywords:
- DEVPATH
- .NET Framework application configuration, assemblies
- application configuration files, specifying assembly's location
- app.config files, assembly locations
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 44d2eadf-7eec-443c-a2ac-d601fd919e17
ms.openlocfilehash: 6fa864f814d6a9ce04f2bce92c61cd0075ab5145
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912993"
---
# <a name="how-to-locate-assemblies-by-using-devpath"></a>方法: DEVPATH を使用してアセンブリを指定する
開発者は、ビルドしている共有アセンブリが複数のアプリケーションで正しく動作することを確認したい場合があります。 開発サイクル中にアセンブリをグローバルアセンブリキャッシュに継続的に配置するのではなく、開発者はアセンブリのビルド出力ディレクトリを指す DEVPATH 環境変数を作成できます。  
  
 たとえば、MySharedAssembly という名前の共有アセンブリを作成し、出力ディレクトリを C:\MySharedAssembly\Debug. にするとします。 C:\MySharedAssembly\Debug を DEVPATH 変数に配置できます。 次に、マシン構成ファイルで[ \<developmentMode >](./file-schema/runtime/developmentmode-element.md)要素を指定する必要があります。 この要素は、アセンブリを検索するために DEVPATH を使用するように共通言語ランタイムに指示します。  
  
 共有アセンブリは、ランタイムによって検出可能である必要があります。  アセンブリ参照を解決するためのプライベートディレクトリを指定するには、「[アセンブリの場所の指定](specify-assembly-location.md)」で説明されているように、構成ファイルの[ \<コードベース > 要素](./file-schema/runtime/codebase-element.md)または[ \<プローブ > 要素](./file-schema/runtime/probing-element.md)を使用します。  また、アセンブリをアプリケーションディレクトリのサブディレクトリに配置することもできます。 詳細については、「 [ランタイムがアセンブリを検索する方法](../deployment/how-the-runtime-locates-assemblies.md)」を参照してください。  
  
> [!NOTE]
> これは高度な機能であり、開発のみを目的としています。  
  
 次の例は、DEVPATH 環境変数によって指定されたディレクトリ内のアセンブリをランタイムが検索する方法を示しています。  
  
## <a name="example"></a>例  
  
```xml  
<configuration>  
  <runtime>  
    <developmentMode developerInstallation="true"/>  
  </runtime>  
</configuration>  
```  
  
 この設定の既定値は false です。  
  
> [!NOTE]
> この設定は、開発時にのみ使用してください。 ランタイムは、DEVPATH で見つかった厳密な名前のアセンブリのバージョンをチェックしません。 単純に、最初に見つかったアセンブリを使用します。  
  
## <a name="see-also"></a>関連項目

- [構成ファイルを使用したアプリの構成](index.md)
