---
title: 秘密キー検索ツール (FindPrivateKey.exe)
ms.date: 09/11/2017
ms.assetid: b8846a95-3fcc-4e8c-b9c0-128d975a6307
ms.openlocfilehash: 316f55b93cf4d867b99878bf483b73cb3f09ad04
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/14/2019
ms.locfileid: "70990355"
---
# <a name="find-private-key-tool-findprivatekeyexe"></a>秘密キー検索ツール (FindPrivateKey.exe)

このコマンド ライン ツールを使用して、証明書ストアから秘密キーを取得できます。 たとえば、 *FindPrivateKey*を使用して、証明書ストア内の特定の x.509 証明書に関連付けられている秘密キーファイルの場所と名前を見つけることができます。

> [!IMPORTANT]
> FindPrivateKey ツールは、WCF のサンプルとして付属しています。 サンプルの場所とビルド方法の詳細については、「 [FindPrivateKey](./samples/findprivatekey.md)」を参照してください。

## <a name="syntax"></a>構文

```console
FindPrivateKey<storeName> <storeLocation> [{ {-n <subjectName>} | {-t <thumbprint>} } [-f | -d | -a]]
```

## <a name="remarks"></a>Remarks

次の表では、秘密キー検索ツール (FindPrivateKey.exe) で使用できる引数とオプションについて説明します。

|引数|説明|
|--------------|-----------------|
|`storeName`|証明書ストアの名前。|
|`storeLocation`|証明書ストアの場所。|

|オプション|説明|
|------------|-----------------|
|`/n <`*subjectName*`>`|証明書のサブジェクト名を指定します。|
|`/t <`*拇印*`>`|証明書のサムプリントを指定します。 Certmgr.exe を使用して証明書のサムプリントを取得します。|
|`/f`|ファイル名だけを出力します。|
|`/d`|ディレクトリだけを出力します。|
|`/a`|絶対ファイル名を出力します。|

## <a name="examples"></a>使用例

John Doe の秘密キーを取得するコマンドを次に示します。

```console
FindPrivateKey My CurrentUser -n "CN=John Doe"
```

次のコマンドは、ローカルコンピューターの秘密キーを取得します。

```console
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52" –a
```
