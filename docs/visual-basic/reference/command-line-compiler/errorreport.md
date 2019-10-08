---
title: -errorreport
ms.date: 08/14/2018
helpviewer_keywords:
- -errorreport compiler option [Visual Basic]
- /errorreport compiler option [Visual Basic]
- errorreport compiler option [Visual Basic]
ms.assetid: a7fe83a2-a6d8-460c-8dad-79a8f433f501
ms.openlocfilehash: c8e193a8cb4d4dbc7515c32139bad9dce8b48ed7
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005621"
---
# <a name="-errorreport"></a>-errorreport

Visual Basic コンパイラが内部コンパイラエラーを報告する方法を指定します。

## <a name="syntax"></a>構文

```console
-errorreport:{ prompt | queue | send | none }
```

## <a name="remarks"></a>コメント

このオプションは、Microsoft の Visual Basic チームに Visual Basic 内部コンパイラエラー (ICE) を報告する便利な方法を提供します。 既定では、コンパイラは Microsoft に情報を送信しません。 ただし、内部コンパイラエラーが発生した場合は、このオプションを使用すると、エラーを Microsoft に報告できます。 この情報は、Microsoft のエンジニアが原因を特定するのに役立ちます。また、Visual Basic の次のリリースの向上に役立つ場合があります。

ユーザーがレポートを送信できるかどうかは、コンピューターとユーザーのポリシーのアクセス許可によって異なります。

次の表は、`-errorreport` オプションの効果をまとめたものです。

|OPTION|動作|
|---|---|
|`prompt`|内部コンパイラエラーが発生した場合は、コンパイラによって収集された正確なデータを表示するためのダイアログボックスが表示されます。 エラー報告に機密情報があるかどうかを確認し、Microsoft に送信するかどうかを決定することができます。 送信する場合、コンピューターとユーザーのポリシー設定によって許可されている場合、コンパイラはデータを Microsoft に送信します。|
|`queue`|エラー レポートを待ち行列に入れます。 管理者特権でログインすると、最後にログインした後に発生したすべてのエラーを報告することができます (エラーの報告を3日ごとに複数回送信するように求めるメッセージは表示されません)。 これは、`-errorreport` オプションが指定されていない場合の既定の動作です。|
|`send`|内部コンパイラエラーが発生し、コンピューターとユーザーのポリシー設定で許可されている場合、コンパイラはデータを Microsoft に送信します。<br /><br /> オプション `-errorreport:send` は、 [Windows エラー報告](/windows/desktop/wer/windows-error-reporting)システム設定によってレポートが有効になっている場合に、エラー情報を Microsoft に自動的に送信しようとします。 |
|`none`|内部コンパイラエラーが発生した場合、そのエラーは収集されず、マイクロソフトに送信されません。|

コンパイラは、エラー発生時にスタックを含むデータを送信します。通常は、ソースコードが含まれています。 [-Bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)オプションと共に `-errorreport` を使用した場合は、ソースファイル全体が送信されます。

このオプションは、Microsoft のエンジニアがエラーをより簡単に再現できるようにするため、 [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)オプションと共に使用することをお勧めします。

> [!NOTE]
> @No__t-0 オプションは、Visual Studio 開発環境内からは使用できません。これは、コマンドラインからコンパイルする場合にのみ使用できます。

## <a name="example"></a>例

次のコードは `T2.vb` のコンパイルを試みます。コンパイラで内部コンパイラエラーが発生した場合は、Microsoft にエラーレポートを送信するように求めるメッセージが表示されます。

```console
vbc -errorreport:prompt t2.vb
```

## <a name="see-also"></a>関連項目

- [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)
- [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [-bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)
