---
title: XmlSerializer によるカスタム シリアル化順序
ms.date: 03/30/2017
ms.assetid: 975abd20-2a1d-42db-aed3-e898025ccce7
ms.openlocfilehash: f63d460163c33c4253cf565a5755babc1030164f
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59295037"
---
# <a name="custom-serialization-order-with-xmlserializer"></a>XmlSerializer によるカスタム シリアル化順序
[サンプルのダウンロード](https://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Xml%20Serialization/CustomOrder.zip.exe)  
  
 このサンプルでは、XML シリアル化で、シリアル化される要素および逆シリアル化される要素の順序を制御する方法を示します。  
  
 シリアル化の詳細については、ソース コード ファイルおよび build.proj ファイル内のコメントを参照してください。  
  
### <a name="to-build-the-sample-using-the-command-prompt"></a>コマンド プロンプトを使用してサンプルをビルドするには  
  
1. コマンド プロンプト ウィンドウを開き、サンプルの使用言語に対応するサブディレクトリに移動します。  
  
2. コマンド ラインで「**msbuild CustomOrder.sln**」と入力します。  
  
### <a name="to-build-the-sample-using-visual-studio"></a>Visual Studio を使用してサンプルをビルドするには  
  
1. [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)]を開き、サンプルが格納されている、言語固有のサブディレクトリのいずれかに移動します。  
  
2. CustomOrder.sln ファイルのアイコンをダブルクリックして、このファイルを Visual Studio で開きます。  
  
3. **[ビルド]** メニューで、**[ソリューションのビルド]** を選択します。  
  
4. サンプル アプリケーションは、既定の \bin ディレクトリまたは \bin\Debug ディレクトリにビルドされます。  
  
## <a name="see-also"></a>関連項目

- [基本的なシリアル化](../../../docs/standard/serialization/basic-serialization.md)
- [バイナリ シリアル化](../../../docs/standard/serialization/binary-serialization.md)
- [属性を使用した XML シリアル化の制御](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md)
- [XML シリアル化の概要](../../../docs/standard/serialization/introducing-xml-serialization.md)
- [シリアル化](../../../docs/standard/serialization/index.md)
- [XML シリアル化および SOAP シリアル化](../../../docs/standard/serialization/xml-and-soap-serialization.md)
