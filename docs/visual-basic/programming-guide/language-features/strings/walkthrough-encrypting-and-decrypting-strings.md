---
title: 文字列の暗号化と複合化
ms.date: 07/20/2015
helpviewer_keywords:
- encryption [Visual Basic], strings
- strings [Visual Basic], encrypting
- decryption [Visual Basic], strings
- strings [Visual Basic], decrypting
ms.assetid: 1f51e40a-2f88-43e2-a83e-28a0b5c0d6fd
ms.openlocfilehash: 36e405c7362993471d3e6da8e319bccb854e1026
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343584"
---
# <a name="walkthrough-encrypting-and-decrypting-strings-in-visual-basic"></a>チュートリアル : Visual Basic での文字列の暗号化と複合化
This walkthrough shows you how to use the <xref:System.Security.Cryptography.DESCryptoServiceProvider> class to encrypt and decrypt strings using the cryptographic service provider (CSP) version of the Triple Data Encryption Standard (<xref:System.Security.Cryptography.TripleDES>) algorithm. The first step is to create a simple wrapper class that encapsulates the 3DES algorithm and stores the encrypted data as a base-64 encoded string. Then, that wrapper is used to securely store private user data in a publicly accessible text file.  
  
 You can use encryption to protect user secrets (for example, passwords) and to make credentials unreadable by unauthorized users. This can protect an authorized user's identity from being stolen, which protects the user's assets and provides non-repudiation. Encryption can also protect a user's data from being accessed by unauthorized users.  
  
 詳細については、「[暗号サービス](../../../../standard/security/cryptographic-services.md)」をご覧ください。  
  
> [!IMPORTANT]
> The Rijndael (now referred to as Advanced Encryption Standard [AES]) and Triple Data Encryption Standard (3DES) algorithms provide greater security than DES because they are more computationally intensive. 詳細については、次のトピックを参照してください。 <xref:System.Security.Cryptography.DES> および <xref:System.Security.Cryptography.Rijndael>  
  
### <a name="to-create-the-encryption-wrapper"></a>To create the encryption wrapper  
  
1. Create the `Simple3Des` class to encapsulate the encryption and decryption methods.  
  
     [!code-vb[VbVbalrStrings#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#38)]  
  
2. Add an import of the cryptography namespace to the start of the file that contains the `Simple3Des` class.  
  
     [!code-vb[VbVbalrStrings#77](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#77)]  
  
3. In the `Simple3Des` class, add a private field to store the 3DES cryptographic service provider.  
  
     [!code-vb[VbVbalrStrings#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#39)]  
  
4. Add a private method that creates a byte array of a specified length from the hash of the specified key.  
  
     [!code-vb[VbVbalrStrings#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#41)]  
  
5. Add a constructor to initialize the 3DES cryptographic service provider.  
  
     The `key` parameter controls the `EncryptData` and `DecryptData` methods.  
  
     [!code-vb[VbVbalrStrings#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#40)]  
  
6. Add a public method that encrypts a string.  
  
     [!code-vb[VbVbalrStrings#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#42)]  
  
7. Add a public method that decrypts a string.  
  
     [!code-vb[VbVbalrStrings#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#43)]  
  
     The wrapper class can now be used to protect user assets. In this example, it is used to securely store private user data in a publicly accessible text file.  
  
### <a name="to-test-the-encryption-wrapper"></a>To test the encryption wrapper  
  
1. In a separate class, add a method that uses the wrapper's `EncryptData` method to encrypt a string and write it to the user's My Documents folder.  
  
     [!code-vb[VbVbalrStrings#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#78)]  
  
2. Add a method that reads the encrypted string from the user's My Documents folder and decrypts the string with the wrapper's `DecryptData` method.  
  
     [!code-vb[VbVbalrStrings#79](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#79)]  
  
3. Add user interface code to call the `TestEncoding` and `TestDecoding` methods.  
  
4. アプリケーションを実行します。  
  
     When you test the application, notice that it will not decrypt the data if you provide the wrong password.  
  
## <a name="see-also"></a>関連項目

- <xref:System.Security.Cryptography>
- <xref:System.Security.Cryptography.DESCryptoServiceProvider>
- <xref:System.Security.Cryptography.DES>
- <xref:System.Security.Cryptography.TripleDES>
- <xref:System.Security.Cryptography.Rijndael>
- [暗号サービス](../../../../standard/security/cryptographic-services.md)
