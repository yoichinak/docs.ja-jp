---
title: -bugreport
ms.date: 03/08/2018
helpviewer_keywords:
- -bugreport compiler option [Visual Basic]
- bugreport compiler option [Visual Basic]
- /bugreport compiler option [Visual Basic]
ms.assetid: e4325406-8dbd-4b48-b311-9ee0799e48bb
ms.openlocfilehash: 46d726332806f7d1f6e80dd7df31867051276b45
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002349"
---
# <a name="-bugreport"></a>-bugreport
バグレポートをファイルするときに使用できるファイルを作成します。  
  
## <a name="syntax"></a>構文  
  
```  
-bugreport:file  
```  
  
## <a name="arguments"></a>引数  
  
|項目|定義|  
|---|---|  
|`file`|必須。 バグレポートを格納するファイルの名前。 名前にスペースが含まれている場合は、ファイル名を引用符 ("") で囲みます。|  
  
## <a name="remarks"></a>コメント  
 次の情報が `file` に追加されます。  
  
- コンパイル内のすべてのソースコードファイルのコピー。  
  
- コンパイルで使用されるコンパイラオプションの一覧。  
  
- コンパイラ、共通言語ランタイム、およびオペレーティングシステムに関するバージョン情報。  
  
- コンパイラの出力 (指定されている場合)。  
  
- 問題の説明。メッセージが表示されます。  
  
- 問題の解決方法についての説明。確認を求めるメッセージが表示されます。  
  
 すべてのソースコードファイルのコピーが `file` に含まれるため、可能な限り短いプログラムで (疑わしい) コードの欠陥を再現することができます。  
  
> [!IMPORTANT]
> @No__t-0 オプションを指定すると、機密情報が含まれる可能性のあるファイルが生成されます。 これには、現在の時刻、コンパイラのバージョン、.NET Framework バージョン、OS バージョン、ユーザー名、コンパイラが実行されたコマンドライン引数、すべてのソースコード、および参照アセンブリのバイナリ形式が含まれます。 このオプションにアクセスするには、web.config ファイルで ASP.NET アプリケーションのサーバー側コンパイルのコマンドラインオプションを指定します。 これを回避するには、machine.config ファイルを変更して、ユーザーがサーバーでコンパイルできないようにします。  
  
 このオプションを `-errorreport:prompt`、`-errorreport:queue`、または `-errorreport:send` と共に使用し、アプリケーションで内部コンパイラエラーが発生した場合は、`file` の情報が Microsoft Corporation に送信されます。 この情報は、Microsoft のエンジニアがエラーの原因を特定するのに役立ちます。また、Visual Basic の次のリリースの向上に役立つ場合があります。 既定では、情報は Microsoft に送信されません。 ただし、既定で有効になっている `-errorreport:queue` を使用してアプリケーションをコンパイルすると、アプリケーションはそのエラーレポートを収集します。 その後、コンピューターの管理者がログインすると、エラー報告システムにポップアップウィンドウが表示され、ログオン後に発生したエラーレポートを管理者が Microsoft に転送できるようになります。  
  
> [!NOTE]
> @No__t-0 オプションは、Visual Studio 開発環境内からは使用できません。これは、コマンドラインからコンパイルする場合にのみ使用できます。  
  
## <a name="example"></a>例  
 次の例では、`T2.vb` をコンパイルし、すべてのバグ報告情報をファイル `Problem.txt` に格納します。  
  
```console  
vbc -bugreport:problem.txt t2.vb  
```  
  
## <a name="see-also"></a>関連項目

- [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)
- [-debug (Visual Basic)](../../../visual-basic/reference/command-line-compiler/debug.md)
- [-errorreport](../../../visual-basic/reference/command-line-compiler/errorreport.md)
- [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Ws-securitypolicy の trustLevel 要素 (ASP.NET Settings スキーマ)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/as399f0x(v=vs.100))
