---
title: Validating Passwords Complexity
ms.date: 07/20/2015
helpviewer_keywords:
- String data type [Visual Basic], validation
ms.assetid: 5d9a918f-6c1f-41a3-a019-b5c2b8ce0381
ms.openlocfilehash: 6e8697379a6fbb5cc15b60291e5b822897c2c013
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348322"
---
# <a name="walkthrough-validating-that-passwords-are-complex-visual-basic"></a>チュートリアル: パスワードの複雑さの検証 (Visual Basic)
This method checks for some strong-password characteristics and updates a string parameter with information about which checks the password fails.  
  
 Passwords can be used in a secure system to authorize a user. However, the passwords must be difficult for unauthorized users to guess. Attackers can use a *dictionary attack* program, which iterates through all of the words in a dictionary (or multiple dictionaries in different languages) and tests whether any of the words work as a user's password. Weak passwords such as "Yankees" or "Mustang" can be guessed quickly. Stronger passwords, such as "?You'L1N3vaFiNdMeyeP@sSWerd!", are much less likely to be guessed. A password-protected system should ensure that users choose strong passwords.  
  
 A strong password is complex (containing a mixture of uppercase, lowercase, numeric, and special characters) and is not a word. This example demonstrates how to verify complexity.  
  
## <a name="example"></a>例  
  
### <a name="code"></a>コード  
 [!code-vb[VbVbcnRegEx#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#1)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 Call this method by passing the string that contains that password.  
  
 この例で必要な要素は次のとおりです。  
  
- <xref:System.Text.RegularExpressions> 名前空間のメンバーへのアクセス許可。 コード内でメンバー名を完全修飾していない場合は、`Imports` ステートメントを追加します。 詳細については、「[Imports ステートメント (.NET 名前空間および型)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)」を参照してください。  
  
## <a name="security"></a>セキュリティ  
 If you're moving the password across a network, you need to use a secure method for transferring data. For more information, see [ASP.NET Web Application Security](https://docs.microsoft.com/previous-versions/aspnet/330a99hc(v=vs.100)).
  
 You can improve the accuracy of the `ValidatePassword` function by adding additional complexity checks:  
  
- Compare the password and its substrings against the user's name, user identifier, and an application-defined dictionary. In addition, treat visually similar characters as equivalent when performing the comparisons. For example, treat the letters "l" and "e" as equivalent to the numerals "1" and "3".  
  
- If there is only one uppercase character, make sure it is not the password's first character.  
  
- Make sure that the last two characters of the password are letter characters.  
  
- Do not allow passwords in which all the symbols are entered from the keyboard's top row.  
  
## <a name="see-also"></a>関連項目

- <xref:System.Text.RegularExpressions.Regex>
- [ASP.NET Web アプリケーションのセキュリティ](https://docs.microsoft.com/previous-versions/aspnet/330a99hc(v=vs.100))
