---
title: COM 相互運用の概要 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- interop assemblies
- COM interop [Visual Basic], about COM interop
ms.assetid: 8bd62e68-383d-407f-998b-29aa0ce0fd67
ms.openlocfilehash: 5eb862d75f8870da40af4cd817fa32a3d2781f38
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592719"
---
# <a name="introduction-to-com-interop-visual-basic"></a>COM 相互運用の概要 (Visual Basic)
コンポーネント オブジェクト モデル (COM) は、他のコンポーネントやアプリケーションをホストする機能を公開するオブジェクトを使用できます。 COM オブジェクトは、Windows が何年ものプログラミングの基盤になっていますが、共通言語ランタイム (CLR) 用に設計されたアプリケーションは、多くの利点を提供します。  
  
 .NET framework アプリケーションは COM に開発したものを置き換える最終的には それまでは、使用または Visual Studio を使用して COM オブジェクトを作成する必要があります。 Com 相互運用性または*COM 相互運用機能*、自分のペースで .NET Framework への移行中に既存の COM オブジェクトを使用することができます。  
  
 COM コンポーネントを作成する .NET Framework を使用して、登録のない COM 相互運用機能を使用できます。 場合に、複数のバージョンがコンピューターにインストールされている、エンドユーザーは XCOPY または FTP を使用してアプリケーションをコンピューターに適切なディレクトリをコピーする実行できます DLL バージョンが有効になっているかを制御できます。 詳細については、次を参照してください。 [Registration-free COM 相互運用機能](../../../framework/interop/registration-free-com-interop.md)します。  
  
## <a name="managed-code-and-data"></a>マネージ コードとデータ  
 コードは、開発、.NET Framework と呼びますの*マネージ コード*、CLR によって使用されるメタデータが含まれています。 .NET Framework アプリケーションで使用されるデータと呼びます*管理対象のデータ*の割り当てとメモリを解放しを実行する型のチェックなど、ランタイムがデータに関連するタスクを管理するためです。 既定では、Visual Basic .NET マネージ コードと、データの使用が、アンマネージ コードと相互運用機能アセンブリを (このページの後半で説明します) を使用して COM オブジェクトのデータにアクセスすることができます。  
  
## <a name="assemblies"></a>アセンブリ  
 アセンブリは、.NET Framework アプリケーションの主な要素です。 ビルド、バージョン管理、および 1 つまたは複数のファイルを含む単一の実装の単位として配置される機能のコレクションになります。 各アセンブリには、アセンブリ マニフェストが含まれています。  
  
## <a name="type-libraries-and-assembly-manifests"></a>タイプ ライブラリとアセンブリのマニフェスト  
 タイプ ライブラリには、メンバー名とデータ型など、COM オブジェクトの特性について説明します。 アセンブリ マニフェストは、.NET Framework アプリケーションの同じ機能を実行します。 これらには、次の情報が含まれます。  
  
- アセンブリ id、バージョン、カルチャ、およびデジタル署名します。  
  
- アセンブリの実装を構成するファイル。  
  
- 型とアセンブリを構成するリソースです。 そこからエクスポートされるものが含まれています。  
  
- 他のアセンブリのコンパイル時の依存関係。  
  
- アセンブリを正しく実行するために必要なアクセス許可。  
  
 アセンブリおよびアセンブリ マニフェストの詳細については、次を参照してください。 [.net アセンブリ](../../../standard/assembly/index.md)します。  
  
### <a name="importing-and-exporting-type-libraries"></a>インポートおよびタイプ ライブラリをエクスポートします。  
 Visual Studio には、タイプ ライブラリから .NET Framework アプリケーションに情報をインポートすることができます、Tlbimp ユーティリティが含まれています。 Tlbexp ユーティリティを使用して、アセンブリからタイプ ライブラリを生成できます。  
  
 Tlbimp と Tlbexp については、次を参照してください。 [Tlbimp.exe (タイプ ライブラリ インポーター)](../../../framework/tools/tlbimp-exe-type-library-importer.md)と[Tlbexp.exe (タイプ ライブラリ エクスポーター)](../../../framework/tools/tlbexp-exe-type-library-exporter.md)します。  
  
## <a name="interop-assemblies"></a>相互運用機能アセンブリ  
 相互運用機能アセンブリは .NET Framework アセンブリ間のブリッジの管理されていると、それと同等の .NET Framework に COM オブジェクトのメンバーを割り当て、アンマネージ コードは、メンバーを管理します。 Visual Basic .NET で作成された相互運用機能アセンブリでは、多くの相互運用マーシャ リングなどの COM オブジェクトの使用の詳細を処理します。  
  
## <a name="interoperability-marshaling"></a>相互運用マーシャ リング  
 すべての .NET Framework アプリケーションでは、ために使用されるプログラミング言語に関係なく、オブジェクトの相互運用性を有効にする一般的な種類のセットを共有します。 パラメーターと戻り値の COM オブジェクトのマネージ コードで使用されるものとは異なるデータ型を使用して場合があります。 *相互運用マーシャ リング*パッケージ パラメーターと戻り値を等価のデータ型のプロセスです。 から COM オブジェクトを移動します。 詳細については、次を参照してください。[相互運用マーシャ リング](../../../framework/interop/interop-marshaling.md)します。  
  
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
