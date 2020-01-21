---
title: 暗号に関する破壊的変更 - .NET Core
description: .NET Core での暗号に関連する破壊的変更の一覧を示します。
ms.date: 09/20/2019
ms.openlocfilehash: 4b13985a12ee0530edd3a0960923aafef1696d90
ms.sourcegitcommit: ed3f926b6cdd372037bbcc214dc8f08a70366390
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2020
ms.locfileid: "76116470"
---
# <a name="cryptography-breaking-changes"></a>暗号での破壊的変更

このページでは、次の破壊的変更について説明します。

- [EnvelopedCms で AES-256 暗号化を既定で使用](#envelopedcms-defaults-to-aes-256-encryption)
- [RSAOpenSsl キー生成の最小サイズの増加](#minimum-size-for-rsaopenssl-key-generation-has-increased)
- [.NET Core 3.0 では、OpenSSL 1.0.x よりも OpenSSL 1.1.x を優先する](#net-core-30-prefers-openssl-11x-to-openssl-10x)
- [Pkcs8PrivateKeyInfo コンストラクターでの引数の検証の改善](#better-argument-validation-in-the-pkcs8privatekeyinfo-constructor)

## <a name="net-core-30"></a>.NET Core 3.0

[!INCLUDE[EnvelopedCms defaults to AES-256 encryption](~/includes/core-changes/cryptography/3.0/envelopedcms-defaults-to-aes256.md)]

***

[!INCLUDE[Minimum size for RSAOpenSsl key generation has increased](~/includes/core-changes/cryptography/3.0/minimum-rsaopenssl-key-size-change.md)]

***

[!INCLUDE[.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x](~/includes/core-changes/cryptography/3.0/net-core-3-0-prefers-openssl-1-1-x.md)]

***

## <a name="net-core-30-preview-9"></a>.NET Core 3.0 Preview 9

[!INCLUDE[Better argument validation in the Pkcs8PrivateKeyInfo constructor](~/includes/core-changes/cryptography/3.0/better-argument-validation-in-pkcs8privatekeyinfo-ctor.md)]

***
