---
title: 厳密な名前付け (アンマネージ API リファレンス)
ms.date: 03/30/2017
helpviewer_keywords:
- strong naming [.NET Framework], using the unmanaged API
- native API reference [.NET Framework], strong naming
- unmanaged API reference [.NET Framework], strong naming
ms.assetid: 428c68b6-a7b4-44be-b280-75905f46612c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 32e74a76b6b1bedee4efc5715d0710c8efce2455
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59120758"
---
# <a name="strong-naming-unmanaged-api-reference"></a>厳密な名前付け (アンマネージ API リファレンス)
厳密な名前付け API を使用すると、アセンブリに対する厳密な名前の署名をクライアントで管理できます。  
  
 厳密な名前を使用してアセンブリに署名すると、アセンブリ マニフェストを格納しているファイルに公開キー暗号化が追加されます。 厳密な名前による署名では、名前の一意性の検証を支援し、名前の悪用を防止し、参照が解決されたときに呼び出し元に一意の ID を提供できます。 しかし、厳密な名前に信頼性のレベルは関連付けられていません。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
> [!NOTE]
>  [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] 以降、これらの関数すべてが非推奨となりました。 推奨されている代わりの関数については、[ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md) インターフェイスを参照してください。  
  
 [GetHashFromAssemblyFile 関数](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromassemblyfile-function.md)  
 指定したハッシュ アルゴリズムを使用して、指定したアセンブリ ファイルのハッシュ値が取得されます。 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 以降、非推奨となっています。  
  
 [GetHashFromAssemblyFileW 関数](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromassemblyfilew-function.md)  
 指定したハッシュ アルゴリズムを使用して、Unicode 文字列として指定したアセンブリ ファイルのハッシュ値が取得されます。 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 以降、非推奨となっています。  
  
 [GetHashFromBlob 関数](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromblob-function.md)  
 指定したハッシュ アルゴリズムを使用して、指定したメモリ アドレスにあるアセンブリのハッシュが取得されます。 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 以降、非推奨となっています。  
  
 [GetHashFromFile 関数](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfile-function.md)  
 指定したファイルの内容に対してハッシュが生成されます。  [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 以降、非推奨となっています。  
  
 [GetHashFromFileW 関数](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfilew-function.md)  
 Unicode 文字列で指定されたファイルの内容に対してハッシュが作成されます。 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 以降、非推奨となっています。  
  
 [GetHashFromHandle 関数](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromhandle-function.md)  
 指定したハッシュ アルゴリズムを使用して、指定したファイル ハンドルを含むファイルの内容に対してハッシュが作成されます。  [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 以降、非推奨となっています。  
  
 [StrongNameCompareAssemblies 関数](../../../../docs/framework/unmanaged-api/strong-naming/strongnamecompareassemblies-function.md)  
 厳密な名前の署名に基づいて 2 つのアセンブリが異なるかどうかが判定されます。 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 以降、非推奨となっています。  
  
 [StrongNameErrorInfo 関数](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md)  
 厳密な名前の関数のいずれかに基づいて最後に発生したエラー コードが取得されます。  
  
 [StrongNameFreeBuffer 関数](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md)  
 [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md)、[StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfrompublickey-function.md)、または[StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md) などの厳密な名前の関数に対する前の呼び出しで割り当てられたメモリが解放されます。   [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 以降、非推奨となっています。  
  
 [StrongNameGetBlob 関数](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetblob-function.md)  
 指定したアドレスにある実行可能ファイルのバイナリ表現が、指定したバッファーに入れられます。 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 以降、非推奨となっています。  
  
 [StrongNameGetBlobFromImage 関数](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetblobfromimage-function.md)  
 指定したメモリ アドレスにあるアセンブリ イメージのバイナリ表現が取得されます。 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 以降、非推奨となっています。  
  
 [StrongNameGetPublicKey 関数](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md)  
 秘密/公開キーの組から公開キーが取得されます。 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 以降、非推奨となっています。  
  
 [StrongNameHashSize 関数](../../../../docs/framework/unmanaged-api/strong-naming/strongnamehashsize-function.md)  
 指定したハッシュ アルゴリズムを使用して、ハッシュに必須のバッファー サイズが取得されます。  [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 以降、非推奨となっています。  
  
 [StrongNameKeyDelete 関数](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeydelete-function.md)  
 指定したキー コンテナーが削除されます。 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 以降、非推奨となっています。  
  
 [StrongNameKeyGen 関数](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeygen-function.md)  
 厳密な名前を使用するために新しい公開/秘密キーの組が作成されます。  [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 以降、非推奨となっています。  
  
 [StrongNameKeyGenEx 関数](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeygenex-function.md)  
 厳密な名前を使用するために、指定したキー サイズによって新しい公開/秘密キーの組が作成されます。 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 以降、非推奨となっています。  
  
 [StrongNameKeyInstall 関数](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeyinstall-function.md)  
 公開/秘密キーの組がコンテナーにインポートされます。  [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 以降、非推奨となっています。  
  
 [StrongNameSignatureGeneration 関数](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md)  
 指定したアセンブリに対して厳密な名前の署名が生成されます。   [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 以降、非推奨となっています。  
  
 [StrongNameSignatureGenerationEx 関数](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegenerationex-function.md)  
 指定したフラグに基づいて、指定したアセンブリに対する厳密な名前の署名が作成されます。    [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 以降、非推奨となっています。  
  
 [StrongNameSignatureSize 関数](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturesize-function.md)  
 厳密な名前の署名のサイズが返されます。 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 以降、非推奨となっています。  
  
 [StrongNameSignatureVerification 関数](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignatureverification-function.md)  
 指定したパスにあるアセンブリ マニフェストに厳密な名前の署名が含まれるかどうかを示す値が取得されます。これは指定したフラグに従って確認されます。 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 以降、非推奨となっています。  
  
 [StrongNameSignatureVerificationEx 関数](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignatureverificationex-function.md)  
 指定したパスにあるアセンブリ マニフェストに厳密な名前の署名が含まれるかどうかを示す値が取得されます。  [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 以降、非推奨となっています。  
  
 [StrongNameSignatureVerificationFromImage 関数](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignatureverificationfromimage-function.md)  
 メモリに既にマップされているアセンブリが、関連付けられている公開キーに対して有効であるかどうかが確認されます。 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 以降、非推奨となっています。  
  
 [StrongNameTokenFromAssembly 関数](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfromassembly-function.md)  
 指定したアセンブリ ファイルから、厳密な名前トークンが作成されます。  [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 以降、非推奨となっています。  
  
 [StrongNameTokenFromAssemblyEx 関数](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfromassemblyex-function.md)  
 指定したアセンブリ ファイルから厳密な名前のトークンが作成され、公開キーが返されます。 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 以降、非推奨となっています。  
  
 [StrongNameTokenFromPublicKey 関数](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfrompublickey-function.md)  
 公開キーを表すトークンが取得されます。 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 以降、非推奨となっています。  
  
 [PublicKeyBlob 構造体](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)  
 公開/秘密キーの組の公開キーがバイナリ形式で表されます。  
  
## <a name="see-also"></a>関連項目

- [ICLRStrongName インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
- [アンマネージ API リファレンス](../../../../docs/framework/unmanaged-api/index.md)
