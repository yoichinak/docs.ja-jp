---
title: '方法: EdmGen.exe を使用してモデル ファイルとマッピング ファイルを生成する'
ms.date: 03/30/2017
ms.assetid: 40db462d-2fd2-4cc1-ad86-d280403e63fa
ms.openlocfilehash: 04606e23cffd03dea956076a07bb6cf2fadb4c9c
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854566"
---
# <a name="how-to-use-edmgenexe-to-generate-the-model-and-mapping-files"></a>方法: EdmGen.exe を使用してモデル ファイルとマッピング ファイルを生成する
このトピックでは、EDM ジェネレーター (EdmGen.exe) ツールを使用して、School データベースに基づく次のファイルを生成する方法について説明します。  
  
- 概念モデル (.csdl ファイル)  
  
- ストレージ モデル (.ssdl ファイル)  
  
- 概念モデルとストレージ モデル間のマッピング (.msl ファイル)  
  
- Visual Basic または C# のオブジェクト レイヤー コード  
  
- ビュー ファイル  
  
 EdmGen.exe ツールでは、/mode:FullGeneration を使用して上記のファイルを生成します。 Edmgen.exe コマンドの詳細については、「 [EDM Generator (edmgen.exe)](edm-generator-edmgen-exe.md)」を参照してください。  
  
 Edmgen.exe を使用してモデルファイルとマッピングファイルを生成する場合でも、Entity Framework を使用するように Visual Studio プロジェクトを構成する必要があります。 詳細については、「[方法 :Entity Framework プロジェクト](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))を手動で構成します。  
  
> [!NOTE]
> EdmGen.exe によって生成された概念モデルには、データベース内のすべてのオブジェクトが含まれています。 特定のオブジェクトだけを含んだ概念モデルを生成する場合は、Entity Data Model ウィザードを使用してください。 詳細については、「[方法 :Entity Data Model ウィザード](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))を使用します。  
  
### <a name="to-generate-the-school-model-for-a-visual-basic-project-using-edmgenexe"></a>EdmGen.exe を使用して Visual Basic プロジェクト用の School モデルを生成するには  
  
1. School データベースを作成します。 詳細については、「 [School サンプルデータベースの作成](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100))」を参照してください。  
  
2. コマンド プロンプトで、次のコマンド (改行なし) を実行します。  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:fullgeneration   
    /c:"Data Source=%datasourceserver%; Initial Catalog=School; Integrated Security=SSPI"   
    /project:School /entitycontainer:SchoolEntities /namespace:SchoolModel /language:VB  
    ```  
  
### <a name="to-generate-the-school-model-for-a-c-project-using-edmgenexe"></a>EdmGen.exe を使用して C# プロジェクト用の School モデルを生成するには  
  
1. School データベースを作成します。 詳細については、「 [School サンプルデータベースの作成](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100))」を参照してください。  
  
2. コマンド プロンプトで、次のコマンド (改行なし) を実行します。  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:fullgeneration   
    /c:"Data Source=%datasourceserver%; Initial Catalog=School; Integrated Security=SSPI"   
    /project:School /entitycontainer:SchoolEntities /namespace:SchoolModel /language:CSharp  
    ```  
  
## <a name="see-also"></a>関連項目

- [モデリングとマッピング](modeling-and-mapping.md)
- [方法: Entity Framework プロジェクトを手動で構成する](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))
- [方法: クエリのパフォーマンスを向上させるためのビューを事前に生成する](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))
- [ADO.NET Entity Data Model ツール](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
- [方法: Edmgen.exe を使用してモデルファイルとマッピングファイルを検証する](how-to-use-edmgen-exe-to-validate-model-and-mapping-files.md)
