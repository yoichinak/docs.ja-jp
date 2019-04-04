---
title: '方法: EdmGen.exe を使用してモデル ファイルとマッピング ファイルを検証するには'
ms.date: 03/30/2017
ms.assetid: 2641906a-971a-4d0b-8aee-13fabc02a1cc
ms.openlocfilehash: 12258236c904c70d6d94490e3d1c6af2457bbe0c
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/07/2019
ms.locfileid: "55827888"
---
# <a name="how-to-use-edmgenexe-to-validate-model-and-mapping-files"></a>方法: EdmGen.exe を使用してモデル ファイルとマッピング ファイルを検証するには
このトピックでは、使用する方法を示します、 [EDM ジェネレーター (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md)モデルとマッピング ファイルを検証するためのツール。 詳細については、[Entity Data Model](../../../../../docs/framework/data/adonet/entity-data-model.md)を参照してください。  
  
### <a name="to-validate-the-school-model-using-edmgenexe"></a>EdmGen.exe を使用して School モデルを検証するには  
  
1.  School データベースを作成します。 詳細については、[School サンプル データベースを作成する](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100))を参照してください。  
  
2.  School モデルを生成します。 詳細については、「[方法 :EdmGen.exe を使用して、モデルとマッピング ファイルを生成する](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)します。  
  
3.  コマンド プロンプトで、次のコマンド (改行なし) を実行します。  
  
    ```console
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:ValidateArtifacts /inssdl:.\School.ssdl /inmsl:.\School.msl /incsdl:.\School.csdl  
    ```  
  
## <a name="see-also"></a>関連項目
- [方法: Entity Framework プロジェクトを手動で構成します。](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))
- [ADO.NET Entity Data Model ツール](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
- [方法: クエリのパフォーマンスを向上させるためにビューを事前に生成します。](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))
- [方法: EdmGen.exe を使用してオブジェクト レイヤー コードを生成するには](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-object-layer-code.md)
