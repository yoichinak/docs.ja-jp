---
title: '方法: エンティティをシリアル化可能にする'
ms.date: 03/30/2017
ms.assetid: a6c5bf6e-064a-4f77-b74c-76b3a5dec309
ms.openlocfilehash: 40a0b4d5a49f88af1bedcbefdd117f6c000b791d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793568"
---
# <a name="how-to-make-entities-serializable"></a>方法: エンティティをシリアル化可能にする
コードを作成するときに、エンティティをシリアル化可能にできます。 エンティティ クラスは <xref:System.Runtime.Serialization.DataContractAttribute> 属性で装飾し、列は <xref:System.Runtime.Serialization.DataMemberAttribute> 属性で装飾します。  
  
 Visual Studio を使用する開発者は、この目的のためにオブジェクトリレーショナルデザイナーを使用できます。  
  
 SQLMetal コマンドラインツールを使用している場合は、 **/シリアル化**オプションを`unidirectional`引数と共に使用します。 詳しくは、「[SqlMetal.exe (コード生成ツール)](../../../../tools/sqlmetal-exe-code-generation-tool.md)」をご覧ください。  
  
## <a name="example"></a>例  
 次の SQLMetal コマンド ラインでは、シリアル化可能なエンティティを持つファイルが作成されます。  
  
```  
sqlmetal /code:nwserializable.vb /language:vb "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
```  
sqlmetal /code:nwserializable.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
## <a name="see-also"></a>関連項目

- [シリアル化](serialization.md)
- [オブジェクト モデルの作成](creating-the-object-model.md)
