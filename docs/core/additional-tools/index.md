---
title: 追加の CLI ツール
description: .NET Core 機能をサポートおよび拡張する、インストール可能な追加ツールについての概要。
author: mlacouture
ms.date: 12/02/2019
ms.custom: mvc
ms.openlocfilehash: 1f066523a24d4e1fd7aaaa5a19e8d6c9d72d35af
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714535"
---
# <a name="net-core-additional-tools-overview"></a>.NET Core の追加ツールの概要

このセクションでは、[.NET Core コマンドライン インターフェイス (CLI)](../tools/index.md) ツールに加え、.NET Core 機能を支援し、拡張するツールを一覧で紹介します。

## <a name="net-core-uninstall-tooluninstall-toolmd"></a>[.NET Core アンインストール ツール](uninstall-tool.md)

[.NET Core アンインストール ツール](https://dotnet.microsoft.com/download/dotnet-core/uninstall-tool) (`dotnet-core-uninstall`) を使うと、システム上の .NET Core SDK とランタイムをクリーンアップし、指定したバージョンのみを残すことができます。 一連のオプションを使用して、アンインストールするバージョンを指定できます。

## <a name="wcf-web-service-reference-toolwcf-web-service-reference-guidemd"></a>[WCF Web Service Reference ツール](wcf-web-service-reference-guide.md)

WCF (Windows Communication Foundation) Web Service Reference は、Visual Studio に接続されているサービス プロバイダーです。[Visual Studio 2017 バージョン 15.5](/visualstudio/releasenotes/vs2017-relnotes-v15.5#WCFTools) から導入されました。 このツールを使うと、現在のソリューションの Web サービス、ネットワーク上の場所、または WSDL ファイルから、メタデータを取得できます。 それにより、.NET Core と互換性のあるソース ファイルが生成され、Web サービス操作へのアクセスに使用できるメソッドを含む WCF プロキシ クラスが定義されます。

## <a name="wcf-dotnet-svcutil-tooldotnet-svcutil-guidemd"></a>[WCF dotnet-svcutil ツール](dotnet-svcutil-guide.md)

WCF (Windows Communication Foundation) の dotnet-svcutil ツールは、ネットワーク上の Web サービスまたは WSDL ファイルからメタデータを取得する .NET Core CLI ツールです。 それにより、.NET Core と互換性のあるソース ファイルが生成され、Web サービス操作へのアクセスに使用できるメソッドを含む WCF プロキシ クラスが定義されます。

**dotnet-svcutil** ツールは、Visual Studio 2017 バージョン 15.5 で最初に用意された Visual Studio 接続済みサービス プロバイダーである、[**WCF Web Service Reference**](wcf-web-service-reference-guide.md) に対する代わりのオプションです。 .NET Core CLI ツールである **dotnet-svcutil** ツールは、Linux、macOS、Windows 上で利用可能なクロスプラットフォームです。

## <a name="wcf-dotnet-svcutilxmlserializer-tooldotnet-svcutilxmlserializer-guidemd"></a>[WCF dotnet-svcutil.xmlserializer ツール](dotnet-svcutil.xmlserializer-guide.md)

.NET Framework 上で、svcutil ツールを使って事前にシリアル化アセンブリを生成することができます。 dotnet-svcutil.xmlserializer NuGet パッケージには、.NET Core 上での同様の機能が用意されています。 これは、クライアント アプリケーション内の型で、WCF サービス コントラクトによって使われ <xref:System.Xml.Serialization.XmlSerializer> によってシリアル化できるものに対して、C# のシリアル化コードを事前に生成します。 これにより、それらの型のオブジェクトをシリアル化または逆シリアル化するときに XML シリアル化の起動時のパフォーマンスが向上します。

## <a name="xml-serializer-generatorxml-serializer-generatormd"></a>[XML シリアライザー ジェネレーター](xml-serializer-generator.md)

.NET Framework の [Xml シリアライザー ジェネレーター (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) と同様に、[Microsoft.XmlSerializer.Generator NuGet パッケージ](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator)は .NET Core および .NET Standard ライブラリのソリューションです。 アセンブリに含まれる型の XML シリアル化アセンブリを作成することで、<xref:System.Xml.Serialization.XmlSerializer> を使用してその型のオブジェクトをシリアル化または逆シリアル化するときの XML シリアル化の起動パフォーマンスを改善します。
