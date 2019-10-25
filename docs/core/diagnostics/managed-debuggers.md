---
title: マネージド デバッガー - .NET Core
description: Visual Studio および Visual Studio Code のマネージド デバッガーの概要。
author: sdmaclea
ms.author: stmaclea
ms.date: 08/05/2019
ms.openlocfilehash: 3741011d22ab6c4240b7f88a9ab790ea61ecd0d2
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "72303648"
---
# <a name="net-core-managed-debuggers"></a>.NET Core マネージド デバッガー

デバッガーを使用すると、プログラムを一時停止したりステップ バイ ステップで実行したりできます。 一時停止すると、プロセスの現在の状態を表示できます。 主要なセクションをステップ実行することにより、コードとその動作の結果が生成される理由を理解することができます。

Microsoft では、**Visual Studio** と **Visual Studio Code** のマネージド コード用のデバッガーを提供しています。

## <a name="visual-studio-managed-debugger"></a>Visual Studio マネージド デバッガー

**Visual Studio** は、最も包括的なデバッガーを利用できる統合開発環境です。 Visual Studio は、Windows で作業する開発者にとって最適な選択肢です。

- [チュートリアル - Visual Studio を使用した Windows での .NET Core アプリケーションのデバッグ](../tutorials/debugging-with-visual-studio.md)

Visual Studio は Windows アプリケーションですが、Linux および macOS アプリをリモートでデバッグするために使用することもできます。

- [Visual Studio を使用した Linux/OSX での .NET Core アプリケーションのデバッグ](https://github.com/Microsoft/MIEngine/wiki/Offroad-Debugging-of-.NET-Core-on-Linux---OSX-from-Visual-Studio)

 ASP.NET Core アプリのデバッグで必要な手順は若干異なります。

- [Visual Studio での ASP.NET Core アプリのデバッグ](/visualstudio/debugger/how-to-enable-debugging-for-aspnet-applications#debug-aspnet-core-apps)

## <a name="visual-studio-code-managed-debugger"></a>Visual Studio Code のマネージド デバッガー

**Visual Studio Code** は、軽量のクロス プラットフォーム コード エディターです。 これは Visual Studio と同じ .NET Core デバッガー実装を使用しますが、簡略化されたユーザー インターフェイスを備えています。

- [チュートリアル - Visual Studio Code を使用した .NET Core アプリケーションのデバッグ](../tutorials/with-visual-studio-code.md#debug)
- [Visual Studio Code でのデバッグ](https://code.visualstudio.com/docs/editor/debugging)
