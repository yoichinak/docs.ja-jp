---
title: パスワードの複雑さ (Visual Basic) を検証しています
ms.date: 07/20/2015
helpviewer_keywords:
- String data type [Visual Basic], validation
ms.assetid: 5d9a918f-6c1f-41a3-a019-b5c2b8ce0381
ms.openlocfilehash: 829d6485acdca22fbf10160c734e5c7f931dd855
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58824937"
---
# <a name="walkthrough-validating-that-passwords-are-complex-visual-basic"></a>チュートリアル: パスワードの複雑な検証 (Visual Basic)
このメソッドは、いくつかの強力なパスワードの特性を確認し、失敗、パスワードをチェックに関する情報を含む文字列パラメーターを更新します。  
  
 パスワードは、ユーザーを承認するために、セキュリティで保護されたシステムで使用できます。 ただし、パスワードは、承認されていないユーザーを推測するが困難である必要があります。 攻撃者が使用できる、*辞書攻撃*プログラムでは、ディクショナリ (または別の言語で複数の辞書) 内の単語のすべてを反復処理し、ユーザーのパスワードとして機能、単語のいずれかであるかどうかをテストします。 「ヤンキース」または「マスタング」などの脆弱なパスワードを簡単に推測できることができます。 強力なパスワードは、たとえば"でしょうか。'L1N3vaFiNdMeyeP@sSWerd!"が大幅に低下を推測できる可能性があります。 パスワードで保護されたシステムでは、ユーザーが強力なパスワードを選択することを確認してください。  
  
 強力なパスワードは、(大文字、小文字、数字、および特殊文字の組み合わせを含む) 複合語ではないです。 この例では、複雑さを検証する方法を示します。  
  
## <a name="example"></a>例  
  
### <a name="code"></a>コード  
 [!code-vb[VbVbcnRegEx#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#1)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 パスワードを格納する文字列を渡すことによって、このメソッドを呼び出します。  
  
 この例で必要な要素は次のとおりです。  
  
-   <xref:System.Text.RegularExpressions> 名前空間のメンバーへのアクセス許可。 コード内でメンバー名を完全修飾していない場合は、`Imports` ステートメントを追加します。 詳細については、「[Imports ステートメント (.NET 名前空間および型)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)」を参照してください。  
  
## <a name="security"></a>セキュリティ  
 パスワードをネットワーク経由で移動する場合は、データを転送するためのセキュリティで保護されたメソッドを使用する必要があります。 詳細については、次を参照してください。 [ASP.NET Web アプリケーションのセキュリティ](https://docs.microsoft.com/previous-versions/aspnet/330a99hc(v=vs.100))します。
  
 精度を向上させることができます、`ValidatePassword`の他の複雑性チェックを追加することで機能します。  
  
-   パスワードとユーザーの名前、ユーザー識別子、およびアプリケーション定義の辞書からその部分文字列を比較します。 さらに、比較を実行するときに、視覚的に類似する文字と同等として扱われます。 たとえば、「1」と「3」の数字と同等として文字"l"と"e"を扱います。  
  
-   1 つだけに大文字がある場合、パスワードの最初の文字ではないことを確認します。  
  
-   パスワードの最後の 2 つの文字がアルファベットの文字であることを確認してください。  
  
-   キーボードの一番上の行からのすべてのシンボルが入力されるパスワードは許可されません。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Text.RegularExpressions.Regex>
- [ASP.NET Web アプリケーションのセキュリティ](https://docs.microsoft.com/previous-versions/aspnet/330a99hc(v=vs.100))
