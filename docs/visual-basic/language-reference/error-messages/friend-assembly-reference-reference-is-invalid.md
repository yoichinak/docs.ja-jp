---
title: フレンド アセンブリ参照 <reference> は無効です
ms.date: 07/20/2015
f1_keywords:
- vbc31535
- bc31535
helpviewer_keywords:
- BC31535
ms.assetid: 6540c1d0-bb19-4051-a579-2e4f9094585e
ms.openlocfilehash: 796c16e912283d86496a4ccbd3b675ac1433f02d
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57356404"
---
# <a name="friend-assembly-reference-reference-is-invalid"></a>フレンド アセンブリ参照\<参照 > が無効です
フレンド アセンブリ参照\<参照 > が無効です。 厳密な名前の署名つきアセンブリはその InternalsVisibleTo 宣言内で公開キーを指定しなければなりません。  
  
 渡すアセンブリ名、<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>属性コンス トラクターは、厳密な名前のアセンブリを識別しますは含まれません、`PublicKey`属性。  
  
 **エラー ID:** BC31535  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  厳密な名前のフレンド アセンブリの公開キーを確認します。 渡されるアセンブリ名の一部として、公開キーを含めて、<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>属性のコンス トラクターを使用して、`PublicKey`属性。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Reflection.AssemblyName>
- [フレンド アセンブリ](../../../standard/assembly/friend-assemblies.md)


