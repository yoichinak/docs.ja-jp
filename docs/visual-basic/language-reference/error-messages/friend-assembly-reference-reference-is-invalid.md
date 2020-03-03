---
title: フレンド アセンブリ参照 <reference> は無効です
ms.date: 07/20/2015
f1_keywords:
- vbc31535
- bc31535
helpviewer_keywords:
- BC31535
ms.assetid: 6540c1d0-bb19-4051-a579-2e4f9094585e
ms.openlocfilehash: 6eb46c6479adc69eaf65b34c69aa69977b4d62ef
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972389"
---
# <a name="friend-assembly-reference-reference-is-invalid"></a>フレンドアセンブリ参照\<の参照 > が無効です
フレンドアセンブリ参照\<の参照 > が無効です。 厳密な名前の署名つきアセンブリはその InternalsVisibleTo 宣言内で公開キーを指定しなければなりません。  
  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>属性コンストラクターに渡されたアセンブリ名は、厳密な名前を持つアセンブリを識別しますが`PublicKey` 、属性は含まれません。  
  
 **エラー ID:** BC31535  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1. 厳密な名前のフレンドアセンブリの公開キーを決定します。 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 属性`PublicKey`を使用して、属性コンストラクターに渡すアセンブリ名の一部として公開キーを含めます。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Reflection.AssemblyName>
- [フレンド アセンブリ](../../../standard/assembly/friend.md)
