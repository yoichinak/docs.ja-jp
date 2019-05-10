---
title: アセンブリの場所の指定
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [.NET Framework], applications
- application configuration [.NET Framework]
- assemblies [.NET Framework], specifying location
ms.assetid: 1cb92bd7-6bab-44cf-8fd3-36303ce84fea
ms.openlocfilehash: 1bfa0ddbeba7546044a0d1ed15f4c2ff303b1491
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64583629"
---
# <a name="specifying-an-assemblys-location"></a>アセンブリの場所の指定
アセンブリの場所を指定する 2 つの方法はあります。  
  
- 使用して、 [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md)要素。  
  
- 使用して、 [ \<probing >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md)要素。  
  
 使用することも、 [.NET Framework 構成ツール (Mscorcfg.msc)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/2bc0cxhc(v=vs.100))アセンブリの場所を指定したり、共通言語ランタイム アセンブリを探すために場所を指定します。  
  
## <a name="using-the-codebase-element"></a>使用して、 \<codeBase > 要素  
 使用することができます、  **\<codeBase >** のみマシン構成またはパブリッシャー ポリシー ファイルでも、アセンブリのバージョンをリダイレクトする要素。 ランタイムを使用するアセンブリ バージョンの決定、バージョンを決定するファイルからコードの基本設定が適用されます。 コード ベースが示されていない場合、ランタイムは、通常の方法でアセンブリをプローブします。 詳細については、次を参照してください。[ランタイムがアセンブリを検索する方法](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)します。  
  
 次の例では、アセンブリの場所を指定する方法を示します。  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
       <dependentAssembly>  
         <assemblyIdentity name="myAssembly"  
                           publicKeyToken="32ab4ba45e0a69a1"  
                           culture="en-us" />  
         <codeBase version="2.0.0.0"  
                   href="http://www.litwareinc.com/myAssembly.dll"/>  
       </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 **バージョン**属性のすべての厳密な名前のアセンブリが必要ですが、アセンブリの厳密な名前が付いていない場合は省略されます。  **\<CodeBase >** 要素が必要です、 **href**属性。 バージョン範囲を指定することはできません、  **\<codeBase >** 要素。  
  
> [!NOTE]
>  厳密な名前ではないアセンブリのコード ベースのヒントを指定する場合、ヒントは、アプリケーション ベースまたはアプリケーション ベース ディレクトリのサブディレクトリにポイントする必要があります。  
  
## <a name="using-the-probing-element"></a>使用して、 \<probing > 要素  
 ランタイムが調査して、コード ベースを持たないアセンブリを検索します。 プローブの詳細については、次を参照してください。[ランタイムがアセンブリを検索する方法](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)します。  
  
 使用することができます、 [ \<probing >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md)ランタイムがアセンブリを検索するときに検索するサブディレクトリを指定するアプリケーション構成ファイル内の要素。 次の例では、ランタイムが検索するディレクトリを指定する方法を示します。  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 **PrivatePath**属性には、ランタイムがアセンブリを検索するディレクトリが含まれています。 アプリケーションが C:\Program \myapp にある場合は、ランタイムが C:\Program Files\MyApp\Bin、C:\Program Files\MyApp\Bin2\Subbin、および C:\Program Files\MyApp\Bin3 コード ベースが指定されていないアセンブリを検索します。 指定したディレクトリ**privatePath**アプリケーション ベース ディレクトリのサブディレクトリにある必要があります。  
  
## <a name="see-also"></a>関連項目

- [共通言語ランタイムのアセンブリ](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
- [アセンブリを使用したプログラミング](../../../docs/framework/app-domains/programming-with-assemblies.md)
- [ランタイムがアセンブリを検索する方法](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [構成ファイルを使用してアプリを構成します。](index.md)
