---
title: COM 相互運用の概要 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- interop assemblies
- COM interop [Visual Basic], about COM interop
ms.assetid: 8bd62e68-383d-407f-998b-29aa0ce0fd67
ms.openlocfilehash: e4421cbc40cdccc1dbbaeb459cb12fda0ee407cf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62022351"
---
# <a name="introduction-to-com-interop-visual-basic"></a>COM 相互運用の概要 (Visual Basic)
コンポーネント オブジェクト モデル (COM) は、他のコンポーネントやアプリケーションをホストする機能を公開するオブジェクトを使用できます。 COM オブジェクトは、Windows が何年ものプログラミングの基盤になっていますが、共通言語ランタイム (CLR) 用に設計されたアプリケーションは、多くの利点を提供します。  
  
 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] アプリケーションが最終的に置き換わります com 開発 それまでは、使用または Visual Studio を使用して COM オブジェクトを作成する必要があります。 Com 相互運用性または*COM 相互運用機能*への移行中に既存の COM オブジェクトを使用することができます、[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]独自のペースでします。  
  
 使用して、 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] COM コンポーネントを作成するには、登録しない COM 相互運用機能を使用することができます。 場合に、複数のバージョンがコンピューターにインストールされている、エンドユーザーは XCOPY または FTP を使用してアプリケーションをコンピューターに適切なディレクトリをコピーする実行できます DLL バージョンが有効になっているかを制御できます。 詳細については、次を参照してください。 [Registration-free COM 相互運用機能](../../../framework/interop/registration-free-com-interop.md)します。  
  
## <a name="managed-code-and-data"></a>マネージ コードとデータ  
 用に開発されたコード、[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]呼びます*マネージ コード*、CLR によって使用されるメタデータが含まれています。 によって使用されるデータ[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]アプリケーションと呼びます*管理対象のデータ*の割り当てとメモリを解放しを実行する型のチェックなど、ランタイムがデータに関連するタスクを管理するためです。 既定では、Visual Basic .NET マネージ コードと、データの使用が、アンマネージ コードと相互運用機能アセンブリを (このページの後半で説明します) を使用して COM オブジェクトのデータにアクセスすることができます。  
  
## <a name="assemblies"></a>アセンブリ  
 アセンブリが、プライマリのビルド ブロック、[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]アプリケーション。 ビルド、バージョン管理、および 1 つまたは複数のファイルを含む単一の実装の単位として配置される機能のコレクションになります。 各アセンブリには、アセンブリ マニフェストが含まれています。  
  
## <a name="type-libraries-and-assembly-manifests"></a>タイプ ライブラリとアセンブリのマニフェスト  
 タイプ ライブラリには、メンバー名とデータ型など、COM オブジェクトの特性について説明します。 アセンブリ マニフェストの同じ機能を実行する[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]アプリケーション。 これらには、次の情報が含まれます。  
  
- アセンブリ id、バージョン、カルチャ、およびデジタル署名します。  
  
- アセンブリの実装を構成するファイル。  
  
- 型とアセンブリを構成するリソースです。 そこからエクスポートされるものが含まれています。  
  
- 他のアセンブリのコンパイル時の依存関係。  
  
- アセンブリを正しく実行するために必要なアクセス許可。  
  
 アセンブリおよびアセンブリ マニフェストの詳細については、次を参照してください。 [.net アセンブリ](../../../standard/assembly/index.md)します。  
  
### <a name="importing-and-exporting-type-libraries"></a>インポートおよびタイプ ライブラリをエクスポートします。  
 Visual Studio にタイプ ライブラリから情報をインポートすることができます、Tlbimp ユーティリティが含まれています、[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]アプリケーション。 Tlbexp ユーティリティを使用して、アセンブリからタイプ ライブラリを生成できます。  
  
 Tlbimp と Tlbexp については、次を参照してください。 [Tlbimp.exe (タイプ ライブラリ インポーター)](../../../framework/tools/tlbimp-exe-type-library-importer.md)と[Tlbexp.exe (タイプ ライブラリ エクスポーター)](../../../framework/tools/tlbexp-exe-type-library-exporter.md)します。  
  
## <a name="interop-assemblies"></a>相互運用機能アセンブリ  
 相互運用機能アセンブリは[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]マネージし、アンマネージ間のブリッジをアセンブリのコードは、それと等価な COM オブジェクト メンバーのマッピング[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]メンバーを管理します。 Visual Basic .NET で作成された相互運用機能アセンブリでは、多くの相互運用マーシャ リングなどの COM オブジェクトの使用の詳細を処理します。  
  
## <a name="interoperability-marshaling"></a>相互運用マーシャ リング  
 すべて[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]アプリケーションのために使用されるプログラミング言語に関係なく、オブジェクトの相互運用性を有効にする一般的な種類のセットを共有します。 パラメーターと戻り値の COM オブジェクトのマネージ コードで使用されるものとは異なるデータ型を使用して場合があります。 *相互運用マーシャ リング*パッケージ パラメーターと戻り値を等価のデータ型のプロセスです。 から COM オブジェクトを移動します。 詳細については、次を参照してください。[相互運用マーシャ リング](../../../framework/interop/interop-marshaling.md)します。  
  
## <a name="see-also"></a>関連項目

- [COM 相互運用](../../../visual-basic/programming-guide/com-interop/index.md)
- [チュートリアル: COM オブジェクトによる継承の実装](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)
- [アンマネージ コードとの相互運用](../../../framework/interop/index.md)
- [相互運用性のトラブルシューティング](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)
- [.NET のアセンブリ](../../../standard/assembly/index.md)
- [Tlbimp.exe (タイプ ライブラリ インポーター)](../../../framework/tools/tlbimp-exe-type-library-importer.md)
- [Tlbexp.exe (タイプ ライブラリ エクスポーター)](../../../framework/tools/tlbexp-exe-type-library-exporter.md)
- [相互運用マーシャリング](../../../framework/interop/interop-marshaling.md)
- [登録を必要としない COM 相互運用機能](../../../framework/interop/registration-free-com-interop.md)
