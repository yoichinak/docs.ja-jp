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
ms.openlocfilehash: 5c4041f42b0a9d1d1e4bc8438e662911534daa42
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775831"
---
# <a name="how-to-locate-assemblies-by-using-devpath"></a>方法: DEVPATH を使用してアセンブリを指定する
開発者は、複数のアプリケーションの構築、共有アセンブリが正常に動作するかどうかを確認することがあります。 継続的に開発サイクル中にグローバル アセンブリ キャッシュにアセンブリを配置ではなく、開発者は、アセンブリのビルド出力ディレクトリを指す DEVPATH 環境変数を作成できます。  
  
 たとえば、MySharedAssembly と呼ばれる共有のアセンブリをビルドして、出力ディレクトリは C:\MySharedAssembly\Debug します。 DEVPATH 変数に C:\MySharedAssembly\Debug を配置することができます。 指定する必要がありますし、 [ \<developmentMode >](../../../docs/framework/configure-apps/file-schema/runtime/developmentmode-element.md)マシン構成ファイル内の要素。 この要素は、アセンブリの検索に DEVPATH を使用する共通言語ランタイムを指示します。  
  
 共有アセンブリは、ランタイムによって探索可能である必要があります。  アセンブリ参照の使用を解決するためのプライベート ディレクトリを指定する、 [ \<codeBase > 要素](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md)または[ \<probing > 要素](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md)」の説明に従って、構成ファイルで[アセンブリの場所を指定する](../../../docs/framework/configure-apps/specify-assembly-location.md)します。  アプリケーション ディレクトリのサブディレクトリにアセンブリを配置することもできます。 詳細については、「 [ランタイムがアセンブリを検索する方法](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)」を参照してください。  
  
> [!NOTE]
>  これは、開発専用の高度な機能です。  
  
 次の例では、ランタイムが DEVPATH 環境変数で指定されたディレクトリでアセンブリを検索する方法を示します。  
  
## <a name="example"></a>例  
  
```xml  
<configuration>  
  <runtime>  
    <developmentMode developerInstallation="true"/>  
  </runtime>  
</configuration>  
```  
  
 この設定の既定値は false。  
  
> [!NOTE]
>  開発時にのみ、この設定を使用します。 ランタイムは、DEVPATH に厳密な名前のアセンブリのバージョンをチェックしません。 単に最初に見つかったアセンブリを使用します。  
  
## <a name="see-also"></a>関連項目

- [構成ファイルを使用してアプリを構成します。](index.md)
