---
title: 暗号化クラスへのアルゴリズム名の割り当て
ms.date: 03/30/2017
helpviewer_keywords:
- mapping algorithm names
- cryptography, mapping algorithm names
- cryptographic algorithms
- names [.NET Framework], algorithm mapping
ms.assetid: 01327c69-c5e1-4ef6-b73f-0a58351f0492
ms.openlocfilehash: 513000169504473aa6dd46feaca214f58502ffd0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912863"
---
# <a name="mapping-algorithm-names-to-cryptography-classes"></a>暗号化クラスへのアルゴリズム名の割り当て
Windows SDK を使用して、開発者が暗号化オブジェクトを作成するには、次の4つの方法があります。  
  
- **New**演算子を使用してオブジェクトを作成します。  
  
- 特定の暗号化アルゴリズムを実装するオブジェクトを作成するには、そのアルゴリズムの抽象クラスで**create**メソッドを呼び出します。  
  
- <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType>メソッドを呼び出して、特定の暗号化アルゴリズムを実装するオブジェクトを作成します。  
  
- アルゴリズムの種類 ( <xref:System.Security.Cryptography.SymmetricAlgorithm>など) の抽象クラスで**create**メソッドを呼び出すことによって、暗号アルゴリズムのクラス (対称ブロック暗号など) を実装するオブジェクトを作成します。  
  
 たとえば、開発者がバイトセットの SHA1 ハッシュを計算するとします。 名前<xref:System.Security.Cryptography>空間には、SHA1 アルゴリズムの2つの実装 (純粋に管理された実装と CryptoAPI をラップする実装) が含まれています。 開発者は、 **new**演算子を呼び出すことによって、 <xref:System.Security.Cryptography.SHA1Managed>特定の SHA1 実装 (など) をインスタンス化することを選択できます。 ただし、クラスで SHA1 ハッシュアルゴリズムが実装されている限り、共通言語ランタイムがどのクラスを読み込むかに関係なく、開発者は<xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType>メソッドを呼び出してオブジェクトを作成できます。 このメソッドは、 **CreateFromName ("CryptoConfig")** を呼び出します。これは、SHA1 ハッシュアルゴリズムの実装を返す必要があります。  
  
 また、 **CryptoConfig**を呼び出すこともできます。これは、既定では、暗号化構成には .NET Framework に出荷されるアルゴリズムの短い名前が含まれているためです。  
  
 どのハッシュアルゴリズムが使用されているかに関係なく、開発者<xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType>はメソッドを呼び出すことができます。このメソッドは、ハッシュ変換を実装するオブジェクトを返します。  
  
## <a name="mapping-algorithm-names-in-configuration-files"></a>構成ファイルでのアルゴリズム名のマッピング  
 既定では、ランタイムは 4 <xref:System.Security.Cryptography.SHA1CryptoServiceProvider>つのシナリオすべてに対してオブジェクトを返します。 ただし、コンピューターの管理者は、最後の2つのシナリオのメソッドが返すオブジェクトの種類を変更できます。 これを行うには、わかりやすいアルゴリズム名をマシン構成ファイル (machine.config) で使用するクラスにマップする必要があります。  
  
 次の例では、 **CryptoConfig、CreateFromName ("SHA1")** 、および HashAlgorithm を実行するようにランタイムを構成する方法を示しています。この例を次に示します。オブジェクトを`MySHA1HashClass`返します。  
  
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
  
 [< Cryptoclass\>要素](./file-schema/cryptography/cryptoclass-element.md)で属性の名前を指定できます (前の例では、属性`MySHA1Hash`に名前を指定します)。 Cryptoclass > 要素の属性 **\<** の値は、共通言語ランタイムがクラスを検索するために使用する文字列です。 [「完全修飾型名の指定](../reflection-and-codedom/specifying-fully-qualified-type-names.md)」で指定した要件を満たす任意の文字列を使用できます。  
  
 多くのアルゴリズム名は、同じクラスにマップできます。 [ \<Nameentry > 要素](./file-schema/cryptography/nameentry-element.md)は、クラスを1つのわかりやすいアルゴリズム名にマップします。 **Name**属性には、 **CryptoConfig**メソッドを呼び出すときに使用される文字列、または<xref:System.Security.Cryptography>名前空間の抽象暗号化クラスの名前を指定できます。 **Class**属性の値は、  **\<cryptoclass >** 要素の属性の名前です。  
  
> [!NOTE]
> Sha1 アルゴリズムを取得するには、 <xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType>または**CryptoConfig CreateFromName ("SHA1")** メソッドを呼び出します。 各メソッドは、SHA1 アルゴリズムを実装するオブジェクトを返すことだけを保証します。 アルゴリズムの各フレンドリ名を、構成ファイル内の同じクラスにマップする必要はありません。  
  
 既定の名前とマップ先のクラスの一覧については<xref:System.Security.Cryptography.CryptoConfig>、「」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [Cryptographic Services](../../standard/security/cryptographic-services.md)
- [暗号化クラスの設定](configure-cryptography-classes.md)
