---
title: .Net を使用してC# JSON をシリアル化および逆シリアル化する
ms.date: 09/16/2019
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 6561d5e1580e1170369622ebc7bb330ff4e0964f
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705783"
---
# <a name="json-serialization-in-net---overview"></a>.NET での JSON のシリアル化-概要

`System.Text.Json` 名前空間は、JavaScript Object Notation (JSON) にシリアル化および逆シリアル化する機能を提供します。

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
* [ソース コード](https://github.com/dotnet/runtime/tree/master/src/libraries/System.Text.Json)
* [API リファレンス](xref:System.Text.Json)
* [ロードマップ](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Text.Json/roadmap/README.md)
* Dotnet/corefx リポジトリでの GitHub の問題
  * [System.string の開発についての説明](https://github.com/dotnet/corefx/issues/33115) <!-- TODO: Issues are still not moved to the new repo-->
  * [すべての system.string の問題](https://github.com/dotnet/runtime/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json)
  * [Json のラベル付きの問題-doc](https://github.com/dotnet/runtime/labels/json-functionality-doc)
