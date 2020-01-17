---
title: .NET での COM 相互運用
description: .NET で COM ライブラリを相互運用する方法について説明します。
ms.date: 07/11/2019
ms.openlocfilehash: 4ea5c2330f8f90d676bfe7003a7307fc38822edf
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706375"
---
# <a name="com-interop-in-net"></a>.NET での COM 相互運用

コンポーネント オブジェクト モデル (COM) では、オブジェクトがその機能を他のコンポーネントに公開し、Windows プラットフォームのアプリケーションをホストすることができます。 ユーザーが既存のコード ベースを使用して相互運用できるように支援するために、.NET Framework は、COM ライブラリとの相互運用に向けて常に強力なサポートを行っています。 .NET Core 3.0 では、このサポートの大部分が、Windows の .NET Core に追加されました。 このドキュメントでは、共通の COM 相互運用テクノロジのしくみと、既存の COM ライブラリとの相互運用に向けたその利用方法について説明します。

- [COM ラッパー](./com-wrappers.md)
- [COM 呼び出し可能ラッパー](./com-callable-wrapper.md)
- [ランタイム呼び出し可能ラッパー](./runtime-callable-wrapper.md)
- [COM 相互運用のための .NET 型の要件](./qualify-net-types-for-interoperation.md)
