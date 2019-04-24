---
title: '方法: アセンブリの内容を表示する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- assembly manifest, viewing information
- Ildasm.exe
- MSIL Disassembler
- assemblies [.NET Framework], viewing contents
- viewing assembly information
- MSIL
- viewing MSIL information
ms.assetid: fb7baaab-4c0d-47ad-8fd3-4591cf834709
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e33fc98f12c1b49d6fe2b1dc187615e2dc9b1768
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59330078"
---
# <a name="how-to-view-assembly-contents"></a>方法: アセンブリの内容を表示する
[Ildasm.exe (IL 逆アセンブラー)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) を使用して、ファイル内の MSIL (Microsoft Intermediate Language) 情報を表示できます。 内容を調べる対象のファイルがアセンブリの場合、この情報にはアセンブリの属性と共に他のモジュールやアセンブリへの参照が含まれることがあります。 この情報は、ファイルがアセンブリまたはアセンブリの一部かどうか、およびファイルに他のモジュールまたはアセンブリへの参照があるかどうかを判断するために役立ちます。  
  
### <a name="to-display-the-contents-of-an-assembly-using-ildasmexe"></a>Ildasm.exe を使用してアセンブリの内容を表示するには  
  
1. コマンド プロンプトに「**ildasm** \<*assembly name*>」と入力します。 たとえば、次のコマンドでは、`Hello.exe` アセンブリが逆アセンブルされます。  
  
    ```  
    ildasm Hello.exe  
    ```  
  
### <a name="to-view-assembly-manifest-information"></a>アセンブリ マニフェストの情報を表示するには  
  
1. MSIL 逆アセンブラー ウィンドウで、マニフェストのアイコンをダブルクリックします。  
  
## <a name="example"></a>例  
 次の例では、基本の "Hello, World" プログラムを使用します。 プログラムをコンパイルした後、Ildasm.exe を使用して Hello.exe アセンブリを逆アセンブルし、アセンブリ マニフェストを表示します。  
  
 [!code-cpp[Conceptual.Assembly.Contents#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.contents/cpp/source.cpp#1)]
 [!code-csharp[Conceptual.Assembly.Contents#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.contents/cs/source.cs#1)]
 [!code-vb[Conceptual.Assembly.Contents#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.contents/vb/source.vb#1)]  
  
 Hello.exe アセンブリに対して ildasm.exe コマンドを実行し、IL DASM ウィンドウでマニフェストのアイコンをダブルクリックすると、次の内容が出力されます。  
  
```  
// Metadata version: v4.0.30319  
.assembly extern mscorlib  
{  
  .publickeytoken = (B7 7A 5C 56 19 34 E0 89 )                         // .z\V.4..  
  .ver 4:0:0:0  
}  
.assembly Hello  
{  
  .custom instance void [mscorlib]System.Runtime.CompilerServices.CompilationRelaxationsAttribute::.ctor(int32) = ( 01 00 08 00 00 00 00 00 )   
  .custom instance void [mscorlib]System.Runtime.CompilerServices.RuntimeCompatibilityAttribute::.ctor() = ( 01 00 01 00 54 02 16 57 72 61 70 4E 6F 6E 45 78   // ....T..WrapNonEx  
                                                                                                             63 65 70 74 69 6F 6E 54 68 72 6F 77 73 01 )       // ceptionThrows.  
  .hash algorithm 0x00008004  
  .ver 0:0:0:0  
}  
.module Hello.exe  
// MVID: {7C2770DB-1594-438D-BAE5-98764C39CCCA}  
.imagebase 0x00400000  
.file alignment 0x00000200  
.stackreserve 0x00100000  
.subsystem 0x0003       // WINDOWS_CUI  
.corflags 0x00000001    //  ILONLY  
// Image base: 0x00600000  
```  
  
 次の表は、例で使用した Hello.exe アセンブリのアセンブリ マニフェストにある各ディレクティブの説明です。  
  
|ディレクティブ|説明|  
|---------------|-----------------|  
|**.assembly extern \<** *assembly name* **>**|現在のモジュールによって参照される項目を含む別のアセンブリを指定します (この例では `mscorlib`)。|  
|**.publickeytoken \<** *token* **>**|参照されるアセンブリの実際のキーのトークンを指定します。|  
|**.ver \<** *version number* **>**|参照されるアセンブリのバージョン番号を指定します。|  
|**.assembly \<** *assembly name* **>**|アセンブリ名を指定します。|  
|**.hash algorithm \<** *int32 value* **>**|使用されるハッシュ アルゴリズムを指定します。|  
|**.ver \<** *version number* **>**|アセンブリのバージョン番号を指定します。|  
|**.module \<** *file name* **>**|アセンブリを構成するモジュールの名前を指定します。 この例では、アセンブリは 1 つのファイルだけで構成されています。|  
|**.subsystem \<** *value* **>**|プログラムに必要なアプリケーション環境を指定します。 この例では、値 3 は、この実行可能ファイルがコンソールで実行されることを示します。|  
|**.corflags**|現在メタデータ内で予約済みのフィールドです。|  
  
 アセンブリ マニフェストは、アセンブリの内容に応じて、多くの異なるディレクティブを格納できます。 アセンブリ マニフェストに含まれる多様なディレクティブの一覧については、ヨーロッパ電子計算機工業会 (ECMA: European Computer Manufacturer Association) のドキュメント、特に「Partition II:Metadata Definition and Semantics」(パーティション II: メタデータの定義とセマンティクス) および「Partition III:CIL Instruction Set」(パーティション III: CIL 命令セット) を参照してください。 ドキュメントはオンラインで入手できます。MSDN の「[ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212)」 (ECMA の C# および共通言語基盤の標準規格) と、ECMA のインターナショナル Web サイトにある「[Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [アプリケーション ドメインとアセンブリ](application-domains.md#application-domains-and-assemblies)
- [アプリケーション ドメインとアセンブリに関する方法のトピック](../../../docs/framework/app-domains/application-domains-and-assemblies-how-to-topics.md)
- [Ildasm.exe (IL 逆アセンブラー)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md)
