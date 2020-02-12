---
title: 基本クラス ライブラリの破壊的変更
description: 基本クラス ライブラリである .NET CoreFx での破壊的変更の一覧を示します。
ms.date: 09/20/2019
ms.openlocfilehash: 9e8a00abfae8bf8f5301a4879cb5274492a2b6fd
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2020
ms.locfileid: "77093085"
---
# <a name="corefx-breaking-changes"></a>CoreFx に関する破壊的変更

CoreFx では、.NET Core で使用されるプリミティブとその他の一般的な型が提供されます。

このページでは、次の破壊的変更について説明します。

- [バージョンをレポートする API が、ファイル バージョンではなく製品をレポートするようになった](#apis-that-report-version-now-report-product-and-not-file-version)
- [カスタム EncoderFallbackBuffer インスタンスが再帰的にフォールバックしない](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively)
- [浮動小数点の書式設定と解析の動作の変更](#floating-point-formatting-and-parsing-behavior-changed)
- [浮動小数点の解析操作が失敗したり OverflowException がスローされたりすることがなくなった](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception)
- [InvalidAsynchronousStateException を別のアセンブリに移動](#invalidasynchronousstateexception-moved-to-another-assembly)
- [.NET Core 3.0 は不正な形式の UTF-8 バイト シーケンスを置換するときに Unicode のベスト プラクティスに従う](#net-core-30-follows-unicode-best-practices-when-replacing-ill-formed-utf-8-byte-sequences)
- [TypeDescriptionProviderAttribute を別のアセンブリに移動](#typedescriptionproviderattribute-moved-to-another-assembly)
- [ZipArchiveEntry による、エントリ サイズに一貫性のないアーカイブ処理の中止](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes)
- [JSON シリアライザーの例外の種類を JsonException から NotSupportedException に変更](#json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception)
- [Utf8JsonWriter での (string)null のセマンティクスの変更](#change-in-semantics-of-stringnull-in-utf8jsonwriter)
- [JsonEncodedText.Encode メソッドに JavaScriptEncoder 引数を追加](#jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument)
- [JsonFactoryConverter.CreateConverter 署名の変更](#jsonfactoryconvertercreateconverter-signature-changed)
- [JsonElement API の変更](#jsonelement-api-changes)
- [組み込みの構造体型にプライベート フィールドを追加](#private-fields-added-to-built-in-struct-types)
- [UseShellExecute の既定値の変更](#change-in-default-value-of-useshellexecute)

## <a name="net-core-30"></a>.NET Core 3.0

[!INCLUDE[APIs that report version now report product and not file version](~/includes/core-changes/corefx/3.0/version-information-changes.md)]

***

[!INCLUDE[Custom EncoderFallbackBuffer instances cannot fall back recursively](~/includes/core-changes/corefx/3.0/custom-encoderfallbackbuffer-cannot-be-recursive.md)]

***

[!INCLUDE[Floating point formatting and parsing behavior changes](~/includes/core-changes/corefx/3.0/floating-point-changes.md)]

***

[!INCLUDE[Floating-point parsing operations no longer fail or throw an OverflowException](~/includes/core-changes/corefx/3.0/floating-point-parsing-does-not-overflow.md)]

***

[!INCLUDE[InvalidAsynchronousStateException moved to another assembly](~/includes/core-changes/corefx/3.0/move-invalidasynchronousstateexception.md)]

***

[!INCLUDE[NET Core 3.0 follows Unicode best practices when replacing ill-formed UTF-8 byte sequences](~/includes/core-changes/corefx/3.0/net-core-3-0-follows-unicode-utf8-best-practices.md)]

***

[!INCLUDE[TypeDescriptionProviderAttribute moved to another assembly](~/includes/core-changes/corefx/3.0/move-typedescriptionproviderattribute.md)]

***

[!INCLUDE[ZipArchiveEntry no longer handles archives with inconsistent entry sizes](~/includes/core-changes/corefx/3.0/ziparchiveentry-and-inconsistent-entry-sizes.md)]

***

## <a name="net-core-30-preview-9"></a>.NET Core 3.0 Preview 9

[!INCLUDE[JSON serializer exception type changed from JsonException to NotSupportedException](~/includes/core-changes/corefx/3.0/serializer-throws-notsupportedexception.md)]

***

## <a name="net-core-30-preview-8"></a>.NET Core 3.0 Preview 8

[!INCLUDE[Change in semantics of (string)null in Utf8JsonWriter](~/includes/core-changes/corefx/3.0/change-in-null-in-utf8jsonwriter.md)]

***

[!INCLUDE[JsonEncodedText.Encode methods have an additional JavaScriptEncoder argument](~/includes/core-changes/corefx/3.0/jsonencodedtext-encode-has-additional-argument.md)]

***

[!INCLUDE[JsonFactoryConverter.CreateConverter signature changed](~/includes/core-changes/corefx/3.0/jsonfactoryconverter-createconverter.md)]

***

## <a name="net-core-30-preview-7"></a>.NET Core 3.0 Preview 7

[!INCLUDE[JsonElement API changes](~/includes/core-changes/corefx/3.0/jsonelement-api-changes.md)]

***

## <a name="net-core-21"></a>.NET Core 2.1

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

***

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***
