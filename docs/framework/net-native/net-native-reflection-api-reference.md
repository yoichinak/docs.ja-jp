---
title: .NET ネイティブ リフレクション API リファレンス
ms.date: 03/30/2017
ms.assetid: 0429c049-22a3-4ba1-9cc8-f6ee91e31d9c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 833d31c48220e2d2b5d07ee482325df090714329
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66052417"
---
# <a name="net-native-reflection-api-reference"></a>.NET ネイティブ リフレクション API リファレンス
.NET ネイティブでは、次の 3 つの新しい例外の種類が含まれます。[System.Runtime.CompilerServices.MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md)、 [System.Reflection.MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md)、および[System.Reflection.MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md). 3 つの例外型すべてについて、次の点に注意してください。  
  
 これらの型は、内部でのみ使用してください。  
 これら 3 つの例外の種類は .NET ネイティブ ツール チェーンでのみ使用されます。 .NET ネイティブ ツール チェーンは、プログラムの実行を継続が許可されない欠落しているデータを検出すると、例外がスローされます。  
  
 これらの例外をコード内で処理しないでください。  
 これらの例外は、アプリケーションで必要なメタデータが存在しないこと ( [MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md) 例外と [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) 例外)、またはアプリケーションで必要な実装コードが欠落していること ( [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) 例外) のどちらかを示します。 これらの例外状態を修正するには、ランタイム ディレクティブ (.rd.xml) ファイルを変更して必要なメタデータまたは実装コードを実行時に使用できるようにします。 詳細については、「 [Runtime Directives (rd.xml) Configuration File Reference](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)」を参照してください。 次の 2 つのトラブルシューティング ツールを使用して、 [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) および [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) 例外を取り除くための適切なエントリをランタイム ディレクティブ ファイルに提供できます。  
  
- [MissingMetadataException トラブルシューティング ツール](https://dotnet.github.io/native/troubleshooter/type.html) (型の場合)。  
  
- [MissingMetadataException トラブルシューティング ツール](https://dotnet.github.io/native/troubleshooter/method.html) (メソッドの場合)。  
  
> [!NOTE]
>  このリファレンスでは、.NET ネイティブに固有の 3 つの例外の種類を説明します。 .NET Framework の主要なリフレクション API のリファレンス ドキュメントについては、次を参照してください。、 <xref:System.Reflection>、<xref:System.Reflection.Context>と<xref:System.Reflection.Emit>名前空間。 .NET Framework の主要な相互運用 API に関するリファレンス ドキュメントについては、「 <xref:System.Runtime.InteropServices>」を参照してください。  
  
## <a name="systemreflection-namespace"></a>System.Reflection 名前空間  
 <xref:System.Reflection> 名前空間には、.NET Framework でリフレクションに使用される主要な型が含まれています。 .NET ネイティブの 2 つの新しい例外の種類も含みます。  
  
|クラス|説明|  
|-----------|-----------------|  
|[MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md)|この例外は、存在しないメタデータを取得するためにリフレクションが使用された場合にスローされます。|  
|[MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md)|この例外は、型または型のメンバーのメタデータは使用可能だが、その実装が削除されている場合にスローされます。|  
  
 この名前空間の他の型に関するドキュメントについては、.NET Framework ドキュメント セットで <xref:System.Reflection> リファレンス ページを参照してください。  
  
## <a name="systemruntimecompilerservices-namespace"></a>System.Runtime.CompilerServices 名前空間  
 <xref:System.Runtime.CompilerServices> 名前空間には、言語コンパイラによって自動的にデザインされた型が含まれています。 .NET ネイティブの新しい例外の種類も含みます。  
  
|クラス|説明|  
|-----------|-----------------|  
|[MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md)|この例外は、手動マーシャリング メソッドが呼び出されたが、型のメタデータがスタティック分析でも、ランタイム ディレクティブ ファイルにも見つからない場合にスローされます。|  
  
 この名前空間の他の型に関するドキュメントについては、.NET Framework ドキュメント セットで <xref:System.Runtime.CompilerServices> リファレンス ページを参照してください。  
  
## <a name="see-also"></a>関連項目

- [MissingInteropDataException クラス](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md)
- [MissingMetadataException クラス](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md)
- [MissingRuntimeArtifactException クラス](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md)
- [はじめに](../../../docs/framework/net-native/getting-started-with-net-native.md)
