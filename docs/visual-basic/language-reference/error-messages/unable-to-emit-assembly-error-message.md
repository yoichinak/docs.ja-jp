---
title: 'アセンブリを作成できません : <error message>'
ms.date: 08/14/2018
f1_keywords:
- vbc30145
- bc30145
helpviewer_keywords:
- BC30145
ms.assetid: 2e7eb2b9-eda6-4bdb-95cc-72c7f0be7528
ms.openlocfilehash: 012284aa42dfa29ad1a5e4ec4a4df5eaacbd4fb7
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65642273"
---
# <a name="unable-to-emit-assembly-error-message"></a>アセンブリを作成できません:\<エラー メッセージ >

Visual Basic コンパイラはアセンブリ リンカーを呼び出す (*Al.exe*Alink とも呼ばれます)、マニフェストと、リンカーでアセンブリを生成する出力段階で、エラーを報告します。

**エラー ID:** BC30145

## <a name="to-correct-this-error"></a>このエラーを解決するには

1. 引用符で囲まれたエラー メッセージを確認し、トピックを参照してください。 [Al.exe](../../../framework/tools/al-exe-assembly-linker.md)のより詳細な説明とアドバイスを参照します。

2. アセンブリを手動で署名を使用して再試行してください、 [Al.exe](../../../framework/tools/al-exe-assembly-linker.md)または[Sn.exe (厳密名ツール)](../../../framework/tools/sn-exe-strong-name-tool.md)します。

3. エラーが続く場合は、状況に関する情報を収集し、マイクロソフト プロダクト サポート サービスに通知してください。

### <a name="to-sign-the-assembly-manually"></a>アセンブリを手動で署名するには

1. 使用して、 [Sn.exe (厳密名ツール)](../../../framework/tools/sn-exe-strong-name-tool.md)) 公開/秘密キー ペア ファイルを作成します。

   このファイルは、 *.snk*拡張機能。

2. エラーが発生している COM 参照をプロジェクトから削除します。

3. 開く、 [Visual Studio 用開発者コマンド プロンプト](../../../framework/tools/developer-command-prompt-for-vs.md)します。

   Windows 10 では、次のように入力します。**開発者コマンド プロンプト**の検索ボックスに、タスク バーにします。 次に、選択**開発者コマンド プロンプト for VS 2017**結果リストから。

4. アセンブリ ラッパーを格納するディレクトリにディレクトリを変更します。

5. 次のコマンドを入力します。

    ```cmd
    tlbimp <path to COM reference file> /out:<output assembly name> /keyfile:<path to .snk file>
    ```

   実際のコマンドを入力する可能性がありますの例を示します。

    ```cmd
    tlbimp c:\windows\system32\msi.dll /out:Interop.WindowsInstaller.dll /keyfile:"c:\documents and settings\mykey.snk"
    ```

   > [!TIP]
   > パスまたはファイルにスペースが含まれている場合は、二重引用符を使用します。

6. Visual Studio で作成したファイルへの参照を .NET アセンブリを追加します。

## <a name="see-also"></a>関連項目

- [Al.exe](../../../framework/tools/al-exe-assembly-linker.md)
- [Sn.exe (厳密名ツール)](../../../framework/tools/sn-exe-strong-name-tool.md)
- [方法: 公開キーと秘密キーのキー ペアを作成する](../../../framework/app-domains/how-to-create-a-public-private-key-pair.md)
- [ご意見](/visualstudio/ide/talk-to-us)
