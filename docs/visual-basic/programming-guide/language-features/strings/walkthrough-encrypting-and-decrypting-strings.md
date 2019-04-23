---
title: Visual Basic における文字列の暗号化および暗号化
ms.date: 07/20/2015
helpviewer_keywords:
- encryption [Visual Basic], strings
- strings [Visual Basic], encrypting
- decryption [Visual Basic], strings
- strings [Visual Basic], decrypting
ms.assetid: 1f51e40a-2f88-43e2-a83e-28a0b5c0d6fd
ms.openlocfilehash: 1d003df87327e14a6cbd65222f86c3dc4df169ff
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59334043"
---
# <a name="walkthrough-encrypting-and-decrypting-strings-in-visual-basic"></a>チュートリアル: Visual Basic における文字列の暗号化および暗号化
このチュートリアルは、使用する方法を示します、<xref:System.Security.Cryptography.DESCryptoServiceProvider>暗号化し、Triple Data Encryption Standard の暗号化サービス プロバイダー (CSP) のバージョンを使用して文字列を復号化するクラス (<xref:System.Security.Cryptography.TripleDES>) アルゴリズム。 最初の手順では、3 des アルゴリズムをカプセル化して、base 64 エンコード文字列として、暗号化されたデータを格納する単純なラッパー クラスを作成します。 次に、そのラッパーを使用して、ユーザーの個人データをパブリックにアクセスできるテキスト ファイルを安全に格納します。  
  
 ユーザー シークレット (パスワードなど) の保護を承認されていないユーザーの資格情報を解読できないようにするには、暗号化を使用することができます。 これは、ユーザーの資産を保護して、否認不可を提供する承認されたユーザーの id が盗まれないを保護できます。 また、暗号化は、承認されていないユーザーへのアクセスをユーザーのデータを保護できます。  
  
 詳細については、「[暗号サービス](../../../../standard/security/cryptographic-services.md)」をご覧ください。  
  
> [!IMPORTANT]
>  (Advanced Encryption Standard [AES] として参照されるようになりました) Rijndael と Triple Data Encryption Standard (3 des) アルゴリズム詳細いるため、DES よりも優れたセキュリティを提供負荷の大きい計算します。 詳細については、次のトピックを参照してください。 <xref:System.Security.Cryptography.DES> および <xref:System.Security.Cryptography.Rijndael>  
  
### <a name="to-create-the-encryption-wrapper"></a>暗号化ラッパーを作成するには  
  
1. 作成、`Simple3Des`暗号化と復号化メソッドをカプセル化するクラス。  
  
     [!code-vb[VbVbalrStrings#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#38)]  
  
2. 含むファイルの先頭に、暗号化の名前空間のインポートを追加、`Simple3Des`クラス。  
  
     [!code-vb[VbVbalrStrings#77](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#77)]  
  
3. `Simple3Des`クラスに 3 des 暗号化サービス プロバイダーを格納するプライベート フィールドを追加します。  
  
     [!code-vb[VbVbalrStrings#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#39)]  
  
4. 指定したキーのハッシュから指定した長さのバイト配列を作成するプライベート メソッドを追加します。  
  
     [!code-vb[VbVbalrStrings#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#41)]  
  
5. 3 des 暗号化サービス プロバイダーを初期化するコンス トラクターを追加します。  
  
     `key`パラメーター コントロール、`EncryptData`と`DecryptData`メソッド。  
  
     [!code-vb[VbVbalrStrings#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#40)]  
  
6. 文字列を暗号化するパブリック メソッドを追加します。  
  
     [!code-vb[VbVbalrStrings#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#42)]  
  
7. 文字列を復号化するパブリック メソッドを追加します。  
  
     [!code-vb[VbVbalrStrings#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#43)]  
  
     ラッパー クラスは、ユーザーの資産を保護するようになりました使用できます。 この例では、パブリックにアクセスできるテキスト ファイルにユーザーの個人データを安全に保管する使用されます。  
  
### <a name="to-test-the-encryption-wrapper"></a>暗号化のラッパーをテストするには  
  
1. 別のクラスのラッパーを使用するメソッドを追加`EncryptData`メソッドは文字列の暗号化をユーザーに書き込むことのマイ ドキュメント フォルダー。  
  
     [!code-vb[VbVbalrStrings#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#78)]  
  
2. ユーザーから、暗号化された文字列を読み取るメソッドのマイ ドキュメント フォルダーと、ラッパーの文字列を復号化を追加`DecryptData`メソッド。  
  
     [!code-vb[VbVbalrStrings#79](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#79)]  
  
3. 呼び出すユーザー インターフェイスのコードを追加、`TestEncoding`と`TestDecoding`メソッド。  
  
4. アプリケーションを実行します。  
  
     アプリケーションをテストする場合は、こと、暗号化は解除されません、データ、間違ったパスワードを指定する場合に注意してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Security.Cryptography>
- <xref:System.Security.Cryptography.DESCryptoServiceProvider>
- <xref:System.Security.Cryptography.DES>
- <xref:System.Security.Cryptography.TripleDES>
- <xref:System.Security.Cryptography.Rijndael>
- [Cryptographic Services](../../../../standard/security/cryptographic-services.md)
