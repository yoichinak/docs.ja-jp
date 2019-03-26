---
title: 暗号化クラスへのアルゴリズム名の割り当て
ms.date: 03/30/2017
helpviewer_keywords:
- mapping algorithm names
- cryptography, mapping algorithm names
- cryptographic algorithms
- names [.NET Framework], algorithm mapping
ms.assetid: 01327c69-c5e1-4ef6-b73f-0a58351f0492
ms.openlocfilehash: 6bf6e79923f0b3119c516ed97e0e86971368a34c
ms.sourcegitcommit: b351b0781a035616c90c68ccae6dd60aae66a953
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/26/2019
ms.locfileid: "55083656"
---
# <a name="mapping-algorithm-names-to-cryptography-classes"></a>暗号化クラスへのアルゴリズム名の割り当て
開発者を使用して暗号化オブジェクトを作成する 4 つの方法がある、 [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)]:  
  
-   使用してオブジェクトを作成、**新しい**演算子。  
  
-   呼び出して、特定の暗号化アルゴリズムを実装するオブジェクトを作成、**作成**するアルゴリズムの抽象クラスのメソッド。  
  
-   呼び出して、特定の暗号化アルゴリズムを実装するオブジェクトを作成、<xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType>メソッド。  
  
-   呼び出して、暗号化アルゴリズム (対称ブロック暗号) などのクラスを実装するオブジェクトを作成、**作成**アルゴリズムの種類の抽象クラスのメソッド (など<xref:System.Security.Cryptography.SymmetricAlgorithm>)。  
  
 たとえば、開発者が、一連のバイトの SHA1 ハッシュを計算するとします。 <xref:System.Security.Cryptography>名前空間には、SHA1 アルゴリズム、1 つの単なるマネージされた実装および CryptoAPI をラップする 1 つの 2 つの実装が含まれています。 開発者は特定の SHA1 実装をインスタンス化を選択できます (など、 <xref:System.Security.Cryptography.SHA1Managed>) 呼び出すことによって、**新しい**演算子。 ただし、クラスは、SHA1 ハッシュ アルゴリズムを実装している限り、共通言語ランタイムがロードするクラス、問題にしない場合、開発者オブジェクトを作成できますを呼び出して、<xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType>メソッド。 このメソッドを呼び出す**System.Security.Cryptography.CryptoConfig.CreateFromName("System.Security.Cryptography.SHA1")**、SHA1 ハッシュ アルゴリズムの実装を返す必要があります。  
  
 開発者が呼び出すことができますも**System.Security.Cryptography.CryptoConfig.CreateFromName("SHA1")** のため、暗号化構成には既定では、.NET Framework に付属しているアルゴリズムの短い名前が含まれています。  
  
 開発者が呼び出すことができる場合、ハッシュ アルゴリズムを使用する必要はありません、<xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType>ハッシュの変換を実装するオブジェクトを返すメソッド。  
  
## <a name="mapping-algorithm-names-in-configuration-files"></a>構成ファイル内のアルゴリズム名のマッピング  
 既定では、ランタイムが返されます、 <xref:System.Security.Cryptography.SHA1CryptoServiceProvider> 4 つのシナリオをすべてのオブジェクト。 ただし、コンピューターの管理者は、最後の 2 つのシナリオで、メソッドが返すオブジェクトの種類を変更できます。 これを行うには、マシン構成ファイル (Machine.config) で使用するクラスにアルゴリズムの表示名をマップする必要があります。  
  
 次の例は、ランタイムを構成する方法を示しますように**System.Security.Cryptography.SHA1.Create**、 **System.Security.CryptoConfig.CreateFromName("SHA1")**、および**System.Security.Cryptography.HashAlgorithm.Create**を返す、`MySHA1HashClass`オブジェクト。  
  
```xml  
<configuration>  
   <!-- Other configuration settings. -->  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass MySHA1Hash="MySHA1HashClass, MyAssembly  
                  Culture='en', PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="SHA1" class="MySHA1Hash"/>  
            <nameEntry name="System.Security.Cryptography.SHA1"  
                       class="MySHA1Hash"/>  
            <nameEntry name="System.Security.Cryptography.HashAlgorithm"  
                       class="MySHA1Hash"/>  
         </cryptoNameMapping>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
 内の属性の名前を指定することができます、 [< cryptoClass\>要素](../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md)(前の例では、名前、属性`MySHA1Hash`)。 内の属性の値、  **\<cryptoClass >** 要素は、共通言語ランタイムを使用して、クラスを検索する文字列。 指定された要件を満たす任意の文字列を使用する[完全修飾型名の指定](../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)します。  
  
 さまざまなアルゴリズムの名前は、同じクラスにマップできます。 [ \<NameEntry > 要素](../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md)クラスを 1 つのアルゴリズムの表示名にマップされます。 **名前**属性を呼び出すときに使用される文字列を指定できます、 **System.Security.Cryptography.CryptoConfig.CreateFromName**メソッド、または、で抽象暗号化クラスの名前<xref:System.Security.Cryptography>名前空間。 値、**クラス**属性は、属性の名前、  **\<cryptoClass >** 要素。  
  
> [!NOTE]
>  SHA1 アルゴリズムを呼び出すことによって取得できます、<xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType>または**Security.CryptoConfig.CreateFromName("SHA1")** メソッド。 各メソッドは、SHA1 アルゴリズムを実装するオブジェクトを返すことのみ保証されます。 構成ファイルで同じクラスに、アルゴリズムのそれぞれの表示名をマップする必要はありません。  
  
 既定の名前とそれをマッピングするクラスの一覧は、<xref:System.Security.Cryptography.CryptoConfig>を参照してください。  
  
## <a name="see-also"></a>関連項目
- [Cryptographic Services](../../../docs/standard/security/cryptographic-services.md)
- [暗号化クラスの設定](../../../docs/framework/configure-apps/configure-cryptography-classes.md)
