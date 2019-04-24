---
title: バージョン間の耐性があるシリアル化に対応する技術サンプル
ms.date: 03/30/2017
ms.assetid: 2a183664-bfbf-4ff0-96f6-c836284ea916
ms.openlocfilehash: d7dfcf7548571d29032495ca8be96db70f2336fc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59308368"
---
# <a name="version-tolerant-serialization-technology-sample"></a>バージョン間の耐性があるシリアル化に対応する技術サンプル
[サンプルのダウンロード](https://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Runtime%20Serialization/VTS.zip.exe)  
  
 このサンプルでは、.NET でのバージョン間の耐性があるシリアル化に対応する機能を示します。 このサンプルでは、バージョンの異なる複数の <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> を使用するアプリケーションをビルドし、データをシリアル化および逆シリアル化します。 さまざまなバージョンがありますが、このアプリケーションではシームレスに処理できます。 詳細については、「[Version Tolerant Serialization](../../../docs/standard/serialization/version-tolerant-serialization.md)」(バージョン トレラントなシリアル化) を参照してください。  
  
### <a name="to-build-the-sample-using-the-command-prompt"></a>コマンド プロンプトを使用してサンプルをビルドするには  
  
1. コマンド プロンプト ウィンドウを表示し、サンプルの使用言語に対応するサブディレクトリ (V1 Application または V2 Application の下) に移動します。  
  
2. コマンド ラインに「**msbuild.exe \<ver> application.sln**」と入力します (この \<ver> は v1 または v2 です)。  
  
### <a name="to-build-the-sample-using-visual-studio"></a>Visual Studio を使用してサンプルをビルドするには  
  
1. [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)]を開き、サンプルが格納されている、言語固有のサブディレクトリのいずれかに移動します。  
  
2. 前の手順で選択したディレクトリの V1 Application サブディレクトリに移動します。  
  
3. V1 Application.sln ファイルのアイコンをダブルクリックして、このファイルを Visual Studio で開きます。  
  
4. **[ビルド]** メニューの **[ソリューションのビルド]** をクリックします。  
  
5. V2 Application サブディレクトリに移動し、前の 2 つの手順を実行して、V2 Application をビルドします。  
  
 各アプリケーションは、既定で、それぞれのプロジェクト ディレクトリの \bin または \bin\Debug サブディレクトリにビルドされます。  
  
### <a name="to-run-the-sample"></a>サンプルを実行するには  
  
1. コマンド プロンプト ウィンドウで、サンプル アプリケーションをビルドしたときに選択した言語に対応する、言語固有のサブディレクトリに移動します。  
  
2. コマンド ラインに「**runme.cmd**」と入力し、両方のアプリケーションを一度に実行します。  
  
 または、新しい実行可能ファイルが格納されているディレクトリに移動し、これらを順に実行します。  
  
> [!NOTE]
>  このサンプルでは、コンソール アプリケーションをビルドします。 出力を表示するには、コマンド プロンプト ウィンドウでこれらを起動し、実行する必要があります。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>
- <xref:System.IO.FileStream>
