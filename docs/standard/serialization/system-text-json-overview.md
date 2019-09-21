---
title: .NET での JSON のシリアル化
author: tdykstra
ms.author: tdykstra
ms.date: 09/16/2019
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.assetid: 4d1111c0-9447-4231-a997-96a2b74b3453
ms.openlocfilehash: 6cb45fded220b6123dbf4461f5f1cf1c3556ff69
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2019
ms.locfileid: "71083094"
---
# <a name="json-serialization-in-net"></a>.NET での JSON のシリアル化

名前`System.Text.Json`空間は、JavaScript Object Notation (JSON) との間でシリアル化およびシリアル化を行うための機能を提供します。

ライブラリの設計では、高度な機能セットに対する高パフォーマンスと低メモリ割り当てが強調されています。 組み込みの UTF-8 サポートは、UTF-8 としてエンコードされた JSON テキストの読み取りと書き込みのプロセスを最適化します。これは、web 上のデータおよびディスク上のファイルのための最も一般的なエンコードです。

ライブラリには、メモリ内のドキュメントオブジェクトモデル (DOM) を操作するためのクラスも用意されています。 この機能により、JSON ファイルまたは文字列内の要素に対する読み取り専用のランダムアクセスが可能になります。 

## <a name="how-to-get-the-library"></a>ライブラリを取得する方法

* このライブラリは、 [.Net Core 3.0](https://aka.ms/netcore3download)共有フレームワークの一部として組み込まれています。
* その他のターゲットフレームワークの場合[は、System.string NuGet パッケージ](https://www.nuget.org/packages/System.Text.Json)をインストールします。 パッケージは次をサポートします。
  * .NET Standard 2.0 以降のバージョン
  * .NET Framework 4.61 以降のバージョン
  * .NET Core 2.0 以降のバージョン

## <a name="additional-resources"></a>その他の技術情報

* [ライブラリの使用方法](system-text-json-how-to.md)
* [ソース コード](https://github.com/dotnet/corefx/tree/master/src/System.Text.Json)
* [API リファレンス](xref:System.Text.Json)
* [ロードマップ](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/roadmap/README.md)
* Dotnet/corefx リポジトリでの GitHub の問題
  * [System.string の開発についての説明](https://github.com/dotnet/corefx/issues/33115)
  * [すべての system.string の問題](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json)
  * [Json のラベル付きの問題-doc](https://github.com/dotnet/corefx/labels/json-functionality-doc)
