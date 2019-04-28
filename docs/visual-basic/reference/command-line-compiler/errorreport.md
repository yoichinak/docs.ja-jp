---
title: -errorreport
ms.date: 08/14/2018
helpviewer_keywords:
- -errorreport compiler option [Visual Basic]
- /errorreport compiler option [Visual Basic]
- errorreport compiler option [Visual Basic]
ms.assetid: a7fe83a2-a6d8-460c-8dad-79a8f433f501
ms.openlocfilehash: 5471f0783eee5e2c14cf0f140094d5c292a73756
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61663259"
---
# <a name="-errorreport"></a>-errorreport

Visual Basic コンパイラが内部コンパイラ エラーを報告する方法を指定します。

## <a name="syntax"></a>構文

```
-errorreport:{ prompt | queue | send | none }
```

## <a name="remarks"></a>Remarks

このオプションは、microsoft Visual Basic チームに Visual Basic 内部コンパイラ エラー (ICE) を報告する便利な手段を提供します。 既定では、コンパイラによってありませんマイクロソフトに情報。 ただし、内部コンパイラ エラーが発生した場合このオプションを使用できます、エラーを Microsoft に報告します。 この情報は、Microsoft のエンジニアが原因の特定に役立つし、Visual Basic の次期リリースの改善に役立てます。

レポートを送信するユーザーの機能は、コンピューターとユーザー ポリシーのアクセス許可によって異なります。

次の表に、効果、`-errorreport`オプション。

|オプション|動作|
|---|---|
|`prompt`|内部コンパイラ エラーが発生する場合は、コンパイラが収集された正確なデータを表示できるように、ダイアログ ボックスが表示されます。 エラー報告の機密情報があるかを判断し、マイクロソフトに送信するかどうかを判断することできます。 送信することを決定するコンピューターおよびユーザー ポリシー設定で許可する場合は、コンパイラは、データを Microsoft に送信します。|
|`queue`|エラー レポートを待ち行列に入れます。 前回のログに記録されたすべてのエラーを報告するには管理者特権でログインすると (ことが求められない 3 日間に 2 回以上のエラー レポートを送信する)。 これは、既定の動作と、`-errorreport`オプションが指定されていません。|
|`send`|内部コンパイラ エラーが発生するコンピューターとユーザー ポリシーの設定で許可する場合は、コンパイラは、データを Microsoft に送信します。<br /><br /> オプション`-errorreport:send`によってレポートが有効になっている場合は、Microsoft にエラー情報を自動的に送信しようとしています、 [Windows エラー報告](/windows/desktop/wer/windows-error-reporting)システムの設定。 |
|`none`|内部コンパイラ エラーが発生する場合、収集またはされませんがマイクロソフトに送信します。|

コンパイラは、通常、いくつかのソース コードを含む、エラー発生時にスタックを含むデータを送信します。 場合`-errorreport`を併用、 [-bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)オプション、ソース ファイル全体が送信されます。

このオプションで最も多く使用、 [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)オプションの詳細は Microsoft のエンジニアが、エラーを簡単に再現できるためです。

> [!NOTE]
> `-errorreport`オプションは、Visual Studio 開発環境内からは使用できません。 コマンドラインからコンパイルする場合にのみ使用可能なです。

## <a name="example"></a>例

次のコードをコンパイルしようとしました。 `T2.vb`、コンパイラには、内部コンパイラ エラーが発生すると、エラー レポートを Microsoft に送信することが確認します。

```
vbc -errorreport:prompt t2.vb
```

## <a name="see-also"></a>関連項目

- [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)
- [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [-bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)
