---
title: .NET ネイティブの一般的なトラブルシューティング
ms.date: 03/30/2017
ms.assetid: ee8c5e17-35ea-48a1-8767-83298caac1e8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f81ff8a347235ab1a765b4f41051dab2da786b89
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59150775"
---
# <a name="net-native-general-troubleshooting"></a>.NET ネイティブの一般的なトラブルシューティング
このトピックでは、[!INCLUDE[net_native](../../../includes/net-native-md.md)]でアプリを開発するときに発生する可能性のある問題のトラブルシューティング方法を説明します。  
  
-   **問題点:** ビルド出力ウィンドウが正しく更新されません。  
  
     **解決方法:** ビルド出力ウィンドウは、ビルドが完了するまで更新されません。 ビルドには数分かかる場合があるため、更新が表示されるまでに遅延が発生することがあります。  
  
-   **問題点:** ARM のアプリの製品版ビルド時間が増加します。  
  
     **解決方法:** ARM デバイスにアプリを展開するときに、[!INCLUDE[net_native](../../../includes/net-native-md.md)]インフラストラクチャが呼び出されます。 このコンパイルは、リフレクションなどの非静的セマンティクスの実行が継続された状態で、多数の最適化を実行します。 さらに、パフォーマンスの最適化のために、.NET Framework でアプリが使用する部分は静的リンクされるため、コンパイルしてネイティブ コードにも含める必要があります。 このため、コンパイルの時間が長くなります。  
  
     ただし、標準的な開発用コンピューター上で、ほとんどのアプリの標準的なコンパイルにかかる時間は 1 分以内です。  通常、標準的な開発用コンピューターでは、.NET Framework のネイティブ イメージを生成するだけで数分かかります。  生成されるコードを改善するための最適化をすべて行い、.NET Framework を含めても、通常、アプリのビルド時間は 1 ～ 2 分です。  
  
     現在も、マルチスレッド コンパイルやその他の最適化を調査して、コンパイルのパフォーマンスを改善する取り組みが続いています。  
  
-   **問題点:** 使用して、アプリがコンパイルされたかどうかはわからない[!INCLUDE[net_native](../../../includes/net-native-md.md)]します。  
  
     **解決方法:** 場合、[!INCLUDE[net_native](../../../includes/net-native-md.md)]コンパイラが呼び出される、ビルド、時間が長くわかりますおよびタスク マネージャーがさまざまな表示[!INCLUDE[net_native](../../../includes/net-native-md.md)]ILC.exe や nutc_driver.exe などのコンポーネントのプロセス。  
  
     [!INCLUDE[net_native](../../../includes/net-native-md.md)] でのプロジェクトのビルドが正常に完了すると、obj\\*config*\ *arch*\\*projectname*.ilc\out に出力が生成されます。最終的なネイティブ パッケージ コンテンツは、bin\\*arch*\\*config*\AppX にあります。 アプリを配置した場合、最終的なネイティブ パッケージ コンテンツは \bin\\*arch*\\*config*\AppX にあります。  
  
-   **問題点:**.NET ネイティブでコンパイルされたアプリは、ランタイムの例外のスロー (通常[MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md)または[MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md)例外) なしでコンパイルするスローされない場合。NET ネイティブです。  
  
     **解決方法:**.NET ネイティブは提供されなかったため、メタデータまたは実装コードはリフレクションを介して使用できる場合は、これらの例外がスローされます。 (詳細については、「[.NET ネイティブとコンパイル](../../../docs/framework/net-native/net-native-and-compilation.md)」を参照してください)。例外を取り除くには、[ランタイム ディレクティブ (rd.xml) ファイル](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)にエントリを追加して、.NET Native ツール チェーンがメタデータまたは実装コードを実行時に使用できるようにする必要があります。 次の 2 つのトラブルシューティング ツールを使用して、ランタイム ディレクティブ ファイルに追加する必要があるエントリを生成できます。  
  
    -   [MissingMetadataException トラブルシューティング ツール](https://dotnet.github.io/native/troubleshooter/type.html) (型の場合)。  
  
    -   [MissingMetadataException トラブルシューティング ツール](https://dotnet.github.io/native/troubleshooter/method.html) (メソッドの場合)。  
  
     詳細については、「[リフレクションおよび .NET ネイティブ](../../../docs/framework/net-native/reflection-and-net-native.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [Windows ストア アプリの .NET ネイティブへの移行](../../../docs/framework/net-native/migrating-your-windows-store-app-to-net-native.md)
