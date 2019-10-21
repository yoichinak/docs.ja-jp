---
title: .Net を使用してC# JSON をシリアル化および逆シリアル化する
author: tdykstra
ms.author: tdykstra
ms.date: 09/16/2019
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.assetid: 4d1111c0-9447-4231-a997-96a2b74b3453
ms.openlocfilehash: 5ce98a7908470a402779436db43333d46f5101fc
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/09/2019
ms.locfileid: "72180152"
---
# <a name="json-serialization-in-net---overview"></a>.NET での JSON のシリアル化-概要

@No__t-0 名前空間は、JavaScript Object Notation (JSON) との間でシリアル化および逆シリアル化を行うための機能を提供します。

ライブラリの設計では、高度な機能セットに対する高パフォーマンスと低メモリ割り当てが強調されています。 組み込みの UTF-8 サポートは、UTF-8 としてエンコードされた JSON テキストの読み取りと書き込みのプロセスを最適化します。これは、web 上のデータおよびディスク上のファイルのための最も一般的なエンコードです。

ライブラリには、メモリ内のドキュメントオブジェクトモデル (DOM) を操作するためのクラスも用意されています。 この機能により、JSON ファイルまたは文字列内の要素に対する読み取り専用のランダムアクセスが可能になります。 

## <a name="how-to-get-the-library"></a>ライブラリを取得する方法

* このライブラリは、 [.Net Core 3.0](https://aka.ms/netcore3download)共有フレームワークの一部として組み込まれています。
* その他のターゲットフレームワークの場合[は、System.string NuGet パッケージ](https://www.nuget.org/packages/System.Text.Json)をインストールします。 パッケージは次をサポートします。
  * .NET Standard 2.0 以降のバージョン
  * 4\.6.1 以降のバージョンの .NET Framework
  * .NET Core 2.0、2.1、および2.2

## <a name="additional-resources"></a>その他の技術情報

* [ライブラリの使用方法](system-text-json-how-to.md)
* [ソース コード](https://github.com/dotnet/corefx/tree/master/src/System.Text.Json)
* [API リファレンス](xref:System.Text.Json)
* [ロードマップ](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/roadmap/README.md)
* Dotnet/corefx リポジトリでの GitHub の問題
  * [System.string の開発についての説明](https://github.com/dotnet/corefx/issues/33115)
  * [すべての system.string の問題](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json)
  * [Json のラベル付きの問題-doc](https://github.com/dotnet/corefx/labels/json-functionality-doc)
