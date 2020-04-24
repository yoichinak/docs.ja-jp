---
title: アセンブリの場所の指定
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [.NET Framework], applications
- application configuration [.NET Framework]
- assemblies [.NET Framework], specifying location
ms.assetid: 1cb92bd7-6bab-44cf-8fd3-36303ce84fea
ms.openlocfilehash: ead69d1e850050214c15295134c06ff6f66e9760
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646032"
---
# <a name="specifying-an-assemblys-location"></a>アセンブリの場所の指定
アセンブリの場所を指定するには、次の 2 つの方法があります。  
  
- [\<コードベース>要素を](./file-schema/runtime/codebase-element.md)使用します。  
  
- [\<プローブ>要素を](./file-schema/runtime/probing-element.md)使用します。  
  
 .NET Framework[構成ツール (Mscorcfg.msc) を](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/2bc0cxhc(v=vs.100))使用して、アセンブリの場所を指定したり、共通言語ランタイムがアセンブリを調査する場所を指定することもできます。  
  
## <a name="using-the-codebase-element"></a>\<コードベース>要素の使用  
 ** \<codeBase>** 要素は、アセンブリのバージョンをリダイレクトするコンピューター構成または発行者ポリシー ファイルでのみ使用できます。 ランタイムは、使用するアセンブリ のバージョンを決定するときに、バージョンを決定するファイルからコード ベースの設定を適用します。 コード ベースが指定されていない場合、ランタイムは通常の方法でアセンブリをプローブします。 詳細については、「[ランタイムがアセンブリを検索する方法](../deployment/how-the-runtime-locates-assemblies.md)」を参照してください。  
  
 アセンブリの場所を指定する方法を次の例に示します。  
  
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
  
 **バージョン**属性は、厳密な名前を持つアセンブリすべてに必要ですが、厳密な名前を持たないアセンブリでは省略する必要があります。 ** \<codeBase>** 要素には**href**属性が必要です。 ** \<codeBase>** 要素でバージョン範囲を指定することはできません。  
  
> [!NOTE]
> 厳密な名前を持たないアセンブリにコード ベース ヒントを指定する場合、ヒントはアプリケーション ベースまたはアプリケーション ベース ディレクトリのサブディレクトリを指している必要があります。  
  
## <a name="using-the-probing-element"></a>プローブ>\<要素の使用  
 ランタイムは、プローブによってコード ベースを持たないアセンブリを検索します。 プローブの詳細については、「[ランタイムがアセンブリを検索する方法](../deployment/how-the-runtime-locates-assemblies.md)」を参照してください。  
  
 アプリケーション構成ファイルの[\<プローブ>](./file-schema/runtime/probing-element.md)要素を使用して、ランタイムがアセンブリを検索するときに検索するサブディレクトリを指定できます。 ランタイムが検索するディレクトリを指定する方法を次の例に示します。  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 **privatePath**属性には、ランタイムがアセンブリを検索するディレクトリが含まれます。 アプリケーションが C:\Program Files\MyApp にある場合、ランタイムは C:\プログラム ファイル\MyApp\Bin、C:\プログラム ファイル\MyApp\Bin2\Subbin、および C:\プログラム ファイル\MyApp\Bin3 でコード ベースを指定していないアセンブリを検索します。 **privatePath**で指定するディレクトリは、アプリケーションベースディレクトリのサブディレクトリでなければなりません。  
  
## <a name="see-also"></a>関連項目

- [.NET のアセンブリ](../../standard/assembly/index.md)
- [アセンブリを使用したプログラミング](../../standard/assembly/index.md)
- [ランタイムがアセンブリを検索する方法](../deployment/how-the-runtime-locates-assemblies.md)
- [構成ファイルを使用してアプリを構成する方法](index.md)
