---
title: .NET ネイティブの概要
ms.date: 03/30/2017
ms.assetid: fc9e04e8-2d05-4870-8cd6-5bd276814afc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1ff4db5216cf984af764176fef636bb586f97c2a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59081490"
---
# <a name="getting-started-with-net-native"></a>.NET ネイティブの概要
Windows 10 用に新しい Windows アプリを作成する場合も、既存の Windows ストア アプリを移行する場合も、次に示す同じ手順を実行することになります。 [!INCLUDE[net_native](../../../includes/net-native-md.md)] アプリを作成するには、次の手順を実行します。  
  
1.  [Windows 10 を対象とするユニバーサル Windows プラットフォーム (UWP) ストア アプリを開発](#Step1)し、アプリのデバッグ ビルドをテストして、そのアプリが適切に動作することを確認します。  
  
2.  [追加のリフレクションおよびシリアル化の使用を処理](#Step2)します。  
  
3.  [リリース ビルドのアプリを展開して、テストします](#Step3)。  
  
4.  [メタデータの欠落を手動で解決し](#Step4)、すべての問題が解決されるまで [手順 3](#Step3) を繰り返します。  
  
> [!NOTE]
>  既存の Windows ストア アプリを [!INCLUDE[net_native](../../../includes/net-native-md.md)]に移行する場合は、「 [Migrating Your Windows Store App to .NET Native](../../../docs/framework/net-native/migrating-your-windows-store-app-to-net-native.md)します。  
  
<a name="Step1"></a>   
## <a name="step-1-develop-and-test-debug-builds-of-your-uwp-app"></a>手順 1: 開発し、UWP アプリのデバッグ ビルドのテスト  
 新しいアプリを開発するか既存のアプリを移行するかに関係なく、Windows アプリについては同じ手順を実行します。  
  
1.  Visual C# または Visual Basic のユニバーサル Windows アプリ テンプレートを使用して、Visual Studio で新しい UWP プロジェクトを作成します。 既定では、すべての UWP アプリケーションは CoreCLR を対象としていて、.NET ネイティブ ツール チェーンを使用してリリース ビルドがコンパイルされます。  
  
2.  UWP アプリ プロジェクトのコンパイルに .NET ネイティブ ツール チェーンを使用する場合と使用しない場合では、両者の間に既知の互換性問題がある点にご注意ください。 詳細については、 [移行ガイド](../../../docs/framework/net-native/migrating-your-windows-store-app-to-net-native.md) を参照してください。  
  
 これで、 [!INCLUDE[net_native](../../../includes/net-native-md.md)] サーフェス領域に対してローカル システム (またはシミュレーター) で実行される C# または Visual Basic コードを作成できるようになりました。  
  
> [!IMPORTANT]
>  アプリを開発するときに、コードでのシリアル化またはリフレクションを使用する場合は注意してください。  
  
 既定では、デバッグ ビルドは F5 キーを押した時に迅速な配置を有効にするために JIT でコンパイルされますが、リリース ビルドは [!INCLUDE[net_native](../../../includes/net-native-md.md)] プリコンパイル テクノロジを使用してコンパイルされます。 つまり、アプリのデバッグ ビルドが正常に動作するようにするには、.NET ネイティブ ツール チェーンでコンパイルする前に、これをビルドしてテストする必要があるということです。  
  
<a name="Step2"></a>   
## <a name="step-2-handle-additional-reflection-and-serialization-usage"></a>手順 2: 追加のリフレクションおよびシリアル化の使用を処理します。  
 プロジェクト作成時に Default.rd.xml という名前のランタイム ディレクティブ ファイルがプロジェクトに自動的に追加されます。 C# で開発する場合、このファイルはプロジェクトの **Properties** フォルダーにあります。 Visual Basic で開発する場合、このファイルはプロジェクトの **My Project** フォルダーにあります。  
  
> [!NOTE]
>  ランタイム ディレクティブ ファイルが必要となる理由の背景を含む .NET ネイティブのコンパイルの概要については、「 [.NET ネイティブとコンパイル](../../../docs/framework/net-native/net-native-and-compilation.md)」をご覧ください。  
  
 ランタイム ディレクティブ ファイルは、アプリの実行時に必要なメタデータを定義するために使用されます。 この既定バージョンのファイルで十分な場合もあります。 ただし、シリアル化やリフレクションに依存するコードには、ランタイム ディレクティブ ファイルに追加のエントリが必要になるものがあります。  
  
 **シリアル化**  
 シリアライザーには 2 つのカテゴリがあり、これらはいずれもランタイム ディレクティブ ファイルに追加エントリを必要とする場合があります。  
  
-   非リフレクション ベースのシリアライザー。 <xref:System.Runtime.Serialization.DataContractSerializer>、 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>、および <xref:System.Xml.Serialization.XmlSerializer> クラスなど、.NET Framework クラス ライブラリ内にあるシリアライザーは、リフレクションに依存しません。 ただし、これらのシリアライザーでは、シリアル化または逆シリアル化されるオブジェクトに基づいてコードが生成される必要があります。  詳しくは、「 [Serialization and Metadata](../../../docs/framework/net-native/serialization-and-metadata.md)」の「Microsoft のシリアライザー」セクションをご覧ください。  
  
-   サードパーティ シリアライザー。 サードパーティのシリアライズ化ライブラリ (Newtonsoft の JSON シリアライザーが最も一般的) は、通常はリフレクション ベースであり、オブジェクトのシリアル化と逆シリアル化をサポートするために *.rd.xml ファイル内のエントリを必要とします。 詳しくは、「 [Serialization and Metadata](../../../docs/framework/net-native/serialization-and-metadata.md)」の「サードパーティ シリアライザー」セクションをご覧ください。  
  
 **リフレクションに依存するメソッド**  
 コードでのリフレクションの使用は明確ではない場合があります。 一般的な API やプログラミング パターンの中には、リフレクション API の一部とは見なされないが、正常な実行にリフレクションを必要とするものがあります。 これには、次のような型インスタンス化およびメソッド作成方法があります。  
  
-   <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> メソッド  
  
-   <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> メソッドと <xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> メソッド  
  
-   <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> メソッド。  
  
 詳細については、「 [APIs That Rely on Reflection](../../../docs/framework/net-native/apis-that-rely-on-reflection.md)」を参照してください。  
  
> [!NOTE]
>  ランタイム ディレクティブ ファイルで使用される型名は完全修飾である必要があります。 たとえば、ファイルでは "String" ではなく "System.String" を指定する必要があります。  
  
<a name="Step3"></a>   
## <a name="step-3-deploy-and-test-the-release-builds-of-your-app"></a>手順 3: 展開し、アプリのリリース ビルドのテスト  
 ランタイム ディレクティブ ファイルを更新したら、アプリのリリース ビルドを再ビルドして配置できます。 .NET ネイティブ バイナリは、プロジェクトの **[プロパティ]** ダイアログ ボックスの **[コンパイル]** タブにある **[ビルド出力パス]** テキスト ボックスに指定されているディレクトリの ILC.out サブディレクトリに配置されています。このフォルダーにないバイナリは、.NET ネイティブでコンパイルされていません。 ターゲット プラットフォームごとに、アプリを十分にテストし、失敗シナリオを含むすべてのシナリオをテストします。  
  
 アプリが正常に動作しない場合 (特にでスロー [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md)または[MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md)実行時に例外)、次の指示に従いますセクションで、[手順 4。メタデータの欠落を手動で解決](#Step4)します。 初回例外を有効にすると、このようなバグの検出に役立ちます。  
  
 アプリのデバッグ ビルドをテストしてデバッグし、 [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) 例外と [MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md) 例外を確実に排除したら、アプリを最適化された [!INCLUDE[net_native](../../../includes/net-native-md.md)] アプリとしてテストする必要があります。 これを行うには、アクティブ プロジェクトの構成を **[デバッグ]** から **[リリース]** に変更します。  
  
<a name="Step4"></a>   
## <a name="step-4-manually-resolve-missing-metadata"></a>手順 4: メタデータの欠落を手動で解決します。  
 デスクトップでは発生せず、 [!INCLUDE[net_native](../../../includes/net-native-md.md)] で発生する最も一般的な失敗は、 [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md)、 [MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md)、または [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) のランタイム例外です。 メタデータの欠落は、予期しない動作やアプリの失敗によって判明することもあります。 このセクションでは、ランタイム ディレクティブ ファイルにディレクティブを追加することによって、これらの例外をデバッグして解決する方法を説明します。 ランタイム ディレクティブの形式については、「[ランタイム ディレクティブ (rd.xml) 構成ファイル リファレンス](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)」を参照してださい。 ランタイム ディレクティブを追加したら、もう一度 [アプリを展開およびテスト](#Step3) して、例外が発生しなくなるまで新しい [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md)、 [MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md)、および  [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) 例外を解決する必要があります。  
  
> [!TIP]
>  高いレベルでランタイム ディレクティブを指定して、アプリがコードの変更に対応できるようにします。  メンバー レベルではなく、名前空間レベルおよび型レベルでランタイム ディレクティブを追加することをお勧めします。 回復性と、バイナリを大きくすることに伴うコンパイル時間の延長の間にはトレードオフがある場合があることに注意してください。  
  
 メタデータの欠落例外に対応する場合は、次のことを確認してください。  
  
-   例外が発生する前にアプリが何を実行しようとしていたか。  
  
    -   たとえば、データ バインド、シリアル化または逆シリアル化を行っていたか、またはリフレクション API を直接使用していましたか。  
  
-   これは特殊なケースか、または他の型でも同じ問題が発生すると考えられるか。  
  
    -   たとえば、 [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) 例外は、アプリのオブジェクト モデル内の型をシリアル化するときにスローされます。  シリアル化されるその他の型がわかっている場合は、それらの型 (または、コードがどの程度構造的に作成されているかによって、それを含む名前空間) に同時にランタイム ディレクティブを追加できます。  
  
-   リフレクションを使用しないようにコードを書き換えることができるか。  
  
    -   たとえば、予期される型がわかっている場合に、コードで `dynamic` キーワードが使用されていますか。  
  
    -   より適切な他の方法を使用できる場合に、リフレクションに依存するメソッドをコードで呼び出していますか。  
  
> [!NOTE]
>  デスクトップ アプリと [!INCLUDE[net_native](../../../includes/net-native-md.md)]でのリフレクションとメタデータの可用性の違いから発生する問題の処理について詳しくは、「 [APIs That Rely on Reflection](../../../docs/framework/net-native/apis-that-rely-on-reflection.md)します。  
  
 アプリのテスト時に発生する例外およびその他の問題の処理に関する具体的な例については、次のページを参照してください。  
  
-   [例:データ バインド時の例外の処理](../../../docs/framework/net-native/example-handling-exceptions-when-binding-data.md)  
  
-   [例:動的プログラミングのトラブルシューティング](../../../docs/framework/net-native/example-troubleshooting-dynamic-programming.md)  
  
-   [.NET ネイティブ アプリでのランタイム例外](../../../docs/framework/net-native/runtime-exceptions-in-net-native-apps.md)  
  
## <a name="see-also"></a>関連項目

- [ランタイム ディレクティブ (rd.xml) 構成ファイル リファレンス](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [.NET ネイティブのセットアップおよび構成](https://docs.microsoft.com/previous-versions/dn600164(v=vs.110))
- [.NET Native とコンパイル](../../../docs/framework/net-native/net-native-and-compilation.md)
- [リフレクションおよび .NET ネイティブ](../../../docs/framework/net-native/reflection-and-net-native.md)
- [リフレクションに依存する API](../../../docs/framework/net-native/apis-that-rely-on-reflection.md)
- [シリアル化とメタデータ](../../../docs/framework/net-native/serialization-and-metadata.md)
- [Windows ストア アプリの .NET ネイティブへの移行](../../../docs/framework/net-native/migrating-your-windows-store-app-to-net-native.md)
