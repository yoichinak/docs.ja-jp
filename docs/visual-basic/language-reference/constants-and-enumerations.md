---
title: 定数と列挙型 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
- constants [Visual Basic]
- constants [Visual Basic], list of
ms.assetid: 309c0ad5-83e4-4f96-99ea-83cd95107417
ms.openlocfilehash: 0a9c01269e12c2d84be4f30c236c439012a88153
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58839590"
---
# <a name="constants-and-enumerations-visual-basic"></a>定数と列挙型 (Visual Basic)
Visual Basic では、さまざまな定義済みの定数と開発者の列挙体を提供します。 定数は、アプリケーションの実行全体で一定の値を格納します。 一連の関連する定数を操作する場合や、定数値に名前を関連付ける場合は、列挙型を使うと便利です。  
  
## <a name="constants"></a>定数  
  
### <a name="conditional-compilation-constants"></a>条件付きコンパイル定数  
 次の表では、条件付きコンパイルで使用できる定義済みの定数を示します。  
  
|**定数**|**説明**|  
|---|---|  
|`CONFIG`|現在の設定に対応する文字列、**アクティブ ソリューション構成**ボックスに、 **Configuration Manager**します。|  
|`DEBUG`|A`Boolean`で設定できる値、**プロジェクト プロパティ** ダイアログ ボックス。 既定では、プロジェクトのデバッグ構成を定義します`DEBUG`します。 ときに`DEBUG`が定義されている<xref:System.Diagnostics.Debug>クラスのメソッドへの出力を生成する、**出力**ウィンドウ。 定義されていない場合<xref:System.Diagnostics.Debug>クラスのメソッドはコンパイルされず、デバッグ出力は生成されません。|  
|`TARGET`|出力の種類のプロジェクトまたはコマンドラインの設定を表す文字列 **/target**オプション。 可能な値`TARGET`は。<br /><br /> -Windows アプリケーションの"winexe"。<br />-"exe"コンソール アプリケーションです。<br />-クラス ライブラリの「ライブラリ」です。<br />-モジュールの「モジュール」。<br />- **/Target**オプションは、Visual Studio 統合開発環境で設定することがあります。 詳細については、次を参照してください。 [/target (Visual Basic)](../../visual-basic/reference/command-line-compiler/target.md)します。|  
|`TRACE`|A`Boolean`で設定できる値、**プロジェクト プロパティ** ダイアログ ボックス。 既定では、プロジェクトのすべての構成を定義`TRACE`します。 ときに`TRACE`が定義されている<xref:System.Diagnostics.Trace>クラスのメソッドへの出力を生成する、**出力**ウィンドウ。 定義されていない場合<xref:System.Diagnostics.Trace>クラスのメソッドはコンパイルされず、いいえ`Trace`出力が生成されます。|  
|`VBC_VER`|Visual Basic バージョンを表す数値*メジャー*.*マイナー*形式。 バージョン番号[!INCLUDE[vbprvblong](~/includes/vbprvblong-md.md)]8.0 です。|  
  
### <a name="print-and-display-constants"></a>印刷と表示の定数  
 印刷を呼び出す関数を表示すると、実際の値の代わりに、コードで、次の定数を使用することができます。  
  
|**定数**|**説明**|  
|---|---|  
|`vbCrLf`|キャリッジ リターンとライン フィード文字の組み合わせ。|  
|`vbCr`|キャリッジ リターン文字。|  
|`vbLf`|ライン フィード文字。|  
|`vbNewLine`|改行文字。|  
|`vbNullChar`|Null 文字です。|  
|`vbNullString`|長さ 0 の文字列とは異なります ("");外部プロシージャを呼び出すために使用します。|  
|`vbObjectError`|エラー番号。 ユーザー定義のエラー番号は、この値より大きくする必要があります。 例:<br /><br /> `Err.Raise(Number) = vbObjectError + 1000`|  
|`vbTab`|タブ文字。|  
|`vbBack`|バック スペース文字。|  
|`vbFormFeed`|Microsoft Windows では使用されません。|  
|`vbVerticalTab`|Microsoft Windows では有用ではないです。|  
  
## <a name="enumerations"></a>列挙  
 次の表では、一覧し、Visual Basic で提供される列挙体について説明します。  
  
|列挙|説明|  
|---|---|  
|<xref:Microsoft.VisualBasic.AppWinStyle>|呼び出すときに呼び出されるプログラムを使用するウィンドウ スタイルを示します、<xref:Microsoft.VisualBasic.Interaction.Shell%2A>関数。|  
|<xref:Microsoft.VisualBasic.AudioPlayMode>|オーディオのメソッドを呼び出すときにサウンドを再生する方法を示します。|  
|<xref:Microsoft.VisualBasic.ApplicationServices.BuiltInRole>|呼び出すときに確認するロールの種類を示す、<xref:Microsoft.VisualBasic.ApplicationServices.User.IsInRole%2A>メソッド。|  
|<xref:Microsoft.VisualBasic.CallType>|呼び出すときに呼び出されるプロシージャの型を示す、<xref:Microsoft.VisualBasic.Interaction.CallByName%2A>関数。|  
|<xref:Microsoft.VisualBasic.CompareMethod>|比較関数を呼び出すときに、文字列を比較する方法を示します。|  
|<xref:Microsoft.VisualBasic.DateFormat>|日付を表示する方法を示すを呼び出すときに、<xref:Microsoft.VisualBasic.Strings.FormatDateTime%2A>関数。|  
|<xref:Microsoft.VisualBasic.DateInterval>|日付関連の関数を呼び出すときに使用する、日付の間隔の決定方法と形式の設定方法を示します。|  
|<xref:Microsoft.VisualBasic.FileIO.DeleteDirectoryOption>|削除するのにはディレクトリには、ファイルまたはディレクトリが含まれている場合に実行する内容を指定します。|  
|<xref:Microsoft.VisualBasic.DueDate>|支払い期日を示します財務メソッドを呼び出すとき。|  
|<xref:Microsoft.VisualBasic.FileIO.FieldType>|テキスト フィールドを区切るかどうか、または固定幅を示します。|  
|<xref:Microsoft.VisualBasic.FileAttribute>|ファイル アクセス関数を呼び出すときに使用するファイル属性を示します。|  
|<xref:Microsoft.VisualBasic.FirstDayOfWeek>|日付関連の関数を呼び出すときに使用する、1 週間の最初の日を示します。|  
|<xref:Microsoft.VisualBasic.FirstWeekOfYear>|日付関連の関数を呼び出すときに使用する年の最初の週を示します。|  
|<xref:Microsoft.VisualBasic.MsgBoxResult>|<xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> 関数によって返され、メッセージ ボックスのどのボタンが押されたかを示します。|  
|<xref:Microsoft.VisualBasic.MsgBoxStyle>|<xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> 関数を呼び出すときに表示するボタンを示します。|  
|<xref:Microsoft.VisualBasic.OpenAccess>|ファイル アクセス関数を呼び出すときに、ファイルを開く方法を示します。|  
|<xref:Microsoft.VisualBasic.OpenMode>|ファイル アクセス関数を呼び出すときに、ファイルを開く方法を示します。|  
|<xref:Microsoft.VisualBasic.OpenShare>|ファイル アクセス関数を呼び出すときに、ファイルを開く方法を示します。|  
|<xref:Microsoft.VisualBasic.FileIO.RecycleOption>|ファイルを完全に削除またはごみ箱に移動するかどうかを指定します。|  
|<xref:Microsoft.VisualBasic.FileIO.SearchOption>|すべてを検索するかどうかを指定しますまたは最上位レベルのディレクトリだけです。|  
|<xref:Microsoft.VisualBasic.TriState>|示す、`Boolean`値または数値書式指定関数を呼び出すときに、既定を使用する必要がありますか。|  
|<xref:Microsoft.VisualBasic.FileIO.UICancelOption>|どのような必要がありますを指定します、ユーザーがクリックした場合は、実行**キャンセル**操作中にします。|  
|<xref:Microsoft.VisualBasic.FileIO.UIOption>|コピー、削除、またはファイルまたはディレクトリを移動するときに、進行状況ダイアログを表示するかどうかを指定します。|  
|<xref:Microsoft.VisualBasic.VariantType>|によって返されるバリアント オブジェクトの型を示す、<xref:Microsoft.VisualBasic.Information.VarType%2A>関数。|  
|<xref:Microsoft.VisualBasic.VbStrConv>|<xref:Microsoft.VisualBasic.Strings.StrConv%2A> 関数の呼び出しで実行する変換の種類を示します。|  
  
## <a name="see-also"></a>関連項目

- [Visual Basic の言語リファレンス](../../visual-basic/language-reference/index.md)
- [Visual Basic](../../visual-basic/index.md)
- [定数の概要](../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [列挙型の概要](../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
