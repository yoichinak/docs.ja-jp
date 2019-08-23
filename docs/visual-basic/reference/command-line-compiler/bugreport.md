---
title: -bugreport
ms.date: 03/08/2018
helpviewer_keywords:
- -bugreport compiler option [Visual Basic]
- bugreport compiler option [Visual Basic]
- /bugreport compiler option [Visual Basic]
ms.assetid: e4325406-8dbd-4b48-b311-9ee0799e48bb
ms.openlocfilehash: 75c3e5842447a8f0812d5a90d7157f7a6a496936
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962445"
---
# <a name="-bugreport"></a>-bugreport
バグレポートをファイルするときに使用できるファイルを作成します。  
  
## <a name="syntax"></a>構文  
  
```  
-bugreport:file  
```  
  
## <a name="arguments"></a>引数  
  
|用語|定義|  
|---|---|  
|`file`|必須。 バグレポートを格納するファイルの名前。 名前にスペースが含まれている場合は、ファイル名を引用符 ("") で囲みます。|  
  
## <a name="remarks"></a>Remarks  
 に`file`次の情報が追加されます。  
  
- コンパイル内のすべてのソースコードファイルのコピー。  
  
- コンパイルで使用されるコンパイラオプションの一覧。  
  
- コンパイラ、共通言語ランタイム、およびオペレーティングシステムに関するバージョン情報。  
  
- コンパイラの出力 (指定されている場合)。  
  
- 問題の説明。メッセージが表示されます。  
  
- 問題の解決方法についての説明。確認を求めるメッセージが表示されます。  
  
 すべてのソースコードファイルのコピーがに`file`含まれているため、可能な限り最短のプログラムでコードの欠陥を再現することができます。  
  
> [!IMPORTANT]
> オプション`-bugreport`を指定すると、機密情報を含むファイルが生成されます。 これには、現在の時刻、コンパイラのバージョン、.NET Framework バージョン、OS バージョン、ユーザー名、コンパイラが実行されたコマンドライン引数、すべてのソースコード、および参照アセンブリのバイナリ形式が含まれます。 このオプションにアクセスするには、web.config ファイルで ASP.NET アプリケーションのサーバー側コンパイルのコマンドラインオプションを指定します。 これを回避するには、machine.config ファイルを変更して、ユーザーがサーバーでコンパイルできないようにします。  
  
 `-errorreport:prompt`このオプションが、 `-errorreport:queue`、または`-errorreport:send`で使用されていて、アプリケーションで内部コンパイラエラーが発生`file`した場合は、の情報が Microsoft Corporation に送信されます。 この情報は、Microsoft のエンジニアがエラーの原因を特定するのに役立ちます。また、Visual Basic の次のリリースの向上に役立つ場合があります。 既定では、情報は Microsoft に送信されません。 ただし、既定で有効になっている`-errorreport:queue`を使用してアプリケーションをコンパイルすると、アプリケーションはそのエラーレポートを収集します。 その後、コンピューターの管理者がログインすると、エラー報告システムにポップアップウィンドウが表示され、ログオン後に発生したエラーレポートを管理者が Microsoft に転送できるようになります。  
  
> [!NOTE]
> この`/bugreport`オプションは、Visual Studio 開発環境内からは使用できません。コマンドラインからコンパイルする場合にのみ使用できます。  
  
## <a name="example"></a>例  
 次の例で`T2.vb`は、すべてのバグ報告情報をコンパイルし`Problem.txt`てファイルに格納します。  
  
```  
vbc -bugreport:problem.txt t2.vb  
```  
  
## <a name="see-also"></a>関連項目

- [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)
- [-debug (Visual Basic)](../../../visual-basic/reference/command-line-compiler/debug.md)
- [-errorreport](../../../visual-basic/reference/command-line-compiler/errorreport.md)
- [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Ws-securitypolicy の trustLevel 要素 (ASP.NET Settings スキーマ)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/as399f0x(v=vs.100))
