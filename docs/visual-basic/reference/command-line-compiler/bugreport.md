---
title: -bugreport
ms.date: 03/08/2018
helpviewer_keywords:
- -bugreport compiler option [Visual Basic]
- bugreport compiler option [Visual Basic]
- /bugreport compiler option [Visual Basic]
ms.assetid: e4325406-8dbd-4b48-b311-9ee0799e48bb
ms.openlocfilehash: e7b4ebc58b6fe9850b92ef945cb0d715e4369efe
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61839567"
---
# <a name="-bugreport"></a>-bugreport
バグ報告を提出するときに使用できるファイルを作成します。  
  
## <a name="syntax"></a>構文  
  
```  
-bugreport:file  
```  
  
## <a name="arguments"></a>引数  
  
|用語|定義|  
|---|---|  
|`file`|必須。 バグ レポートを格納するファイルの名前。 ファイル名を引用符で囲みます ("")、名前にスペースが含まれている場合。|  
  
## <a name="remarks"></a>Remarks  
 次の情報に追加されます`file`:  
  
-   コンパイルですべてのソース コード ファイルのコピー。  
  
-   コンパイルで使用されるコンパイラ オプションの一覧。  
  
-   コンパイラ、共通言語ランタイム、およびオペレーティング システムのバージョン情報。  
  
-   コンパイラの出力 (指定されている場合)。  
  
-   求められることが、問題の説明です。  
  
-   求められることが問題をどのように考えるの説明を修正する必要があります。  
  
 内のすべてのソース コード ファイルのコピーが含まれているため`file`、できるだけ小さなプログラムで (疑わしい) コード障害を再現したい場合があります。  
  
> [!IMPORTANT]
>  `-bugreport`オプションは、機密性の高い情報を含むファイルを生成します。 これにより、コンパイラのバージョン、現在の時刻が含まれます。[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]バージョン、OS のバージョン、ユーザー名、、のコマンドライン引数をコンパイラが実行されたすべてのソース コードと参照アセンブリのいずれかのバイナリ形式です。 このオプションは、Web.config ファイルのサーバー側のコンパイルでのコマンド ライン オプションを指定することでアクセスできる、[!INCLUDE[vstecasp](~/includes/vstecasp-md.md)]アプリケーション。 これを回避するには、サーバーでのコンパイルからユーザーを禁止する Machine.config ファイルを変更します。  
  
 このオプションを使用した場合`-errorreport:prompt`、 `-errorreport:queue`、または`-errorreport:send`、アプリケーションでの情報は、内部コンパイラ エラーが発生して`file`Microsoft Corporation に送信されます。 この情報は、Microsoft のエンジニアが、エラーの原因の特定に役立つし、Visual Basic の次期リリースの改善に役立てます。 既定では、Microsoft に情報は送信されません。 ただしを使用してアプリケーションをコンパイルするときに`-errorreport:queue`アプリケーションは、エラー レポートを収集、既定で有効になっています。 次に、コンピューターの管理者がログインすると、エラー レポート システムにログオン以降に発生したエラー レポートをマイクロソフトに送信できるようにするポップアップ ウィンドウが表示されます。  
  
> [!NOTE]
>  `/bugreport`オプションは、Visual Studio 開発環境内からは使用できません。 コマンドラインからコンパイルするときにのみ、は使用できます。  
  
## <a name="example"></a>例  
 次の例をコンパイル`T2.vb`バグ レポートのすべての情報をファイルに格納`Problem.txt`します。  
  
```  
vbc -bugreport:problem.txt t2.vb  
```  
  
## <a name="see-also"></a>関連項目

- [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)
- [-デバッグ (Visual Basic)](../../../visual-basic/reference/command-line-compiler/debug.md)
- [-errorreport](../../../visual-basic/reference/command-line-compiler/errorreport.md)
- [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [(ASP.NET 設定スキーマ) securityPolicy の trustLevel 要素](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/as399f0x(v=vs.100))
