---
title: .NET での COM 相互運用
description: .NET で COM ライブラリを相互運用する方法について説明します。
author: jkoritzinsky
ms.author: jekoritz
ms.date: 07/11/2019
ms.openlocfilehash: 03ede2fc95f4114a4d80423bd7de2e46012a2431
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "68631426"
---
# <a name="com-interop-in-net"></a>.NET での COM 相互運用

コンポーネント オブジェクト モデル (COM) では、オブジェクトがその機能を他のコンポーネントに公開し、Windows プラットフォームのアプリケーションをホストすることができます。 ユーザーが既存のコード ベースを使用して相互運用できるように支援するために、.NET Framework は、COM ライブラリとの相互運用に向けて常に強力なサポートを行っています。 .NET Core 3.0 では、このサポートの大部分が、Windows の .NET Core に追加されました。 このドキュメントでは、共通の COM 相互運用テクノロジのしくみと、既存の COM ライブラリとの相互運用に向けたその利用方法について説明します。

- [COM ラッパー](./com-wrappers.md)
- [COM 呼び出し可能ラッパー](./com-callable-wrapper.md)
- [ランタイム呼び出し可能ラッパー](./runtime-callable-wrapper.md)
- [COM 相互運用のための .NET 型の要件](./qualify-net-types-for-interoperation.md)
