---
title: アセンブリ '<assembly1>' からの間接参照により、埋め込まれた相互運用機能アセンブリ '<assembly2>' の参照が作成されました。
ms.date: 07/20/2015
f1_keywords:
- vbc40059
- bc40059
helpviewer_keywords:
- VBC40059
- BC40059
ms.assetid: 520e39cb-8ab6-46f5-aa00-08afd51b4b7c
ms.openlocfilehash: c0b4f56e3d1613486dd1198976557831ce657e1b
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58837547"
---
# <a name="a-reference-was-created-to-embedded-interop-assembly-assembly1-because-of-an-indirect-reference-to-that-assembly-from-assembly-assembly2"></a>埋め込まれた相互運用機能アセンブリへの参照が作成された '\<assembly1 >' のアセンブリからそのアセンブリへの間接参照により'\<assembly2 >'
埋め込まれた相互運用機能アセンブリ '\<assembly1>' への参照が作成されました。これは、そのアセンブリへの間接参照がアセンブリ '\<assembly2>' によって作成されたためです。 両方のアセンブリで '相互運用機能型の埋め込み' プロパティを変更することを検討してください。  
  
 `Embed Interop Types` プロパティが `True` に設定されたアセンブリ (assembly1) に参照を追加しました。 これにより、コンパイラは、このアセンブリから相互運用機能の型情報を埋め込むよう指示されます。 ただし、参照していた別のアセンブリ (assembly2) もこのアセンブリ (assembly1) を参照しており、また `Embed Interop Types` プロパティが `False` に設定されているため、コンパイラはこのアセンブリから相互運用機能の型情報を埋め込むことができません。  
  
> [!NOTE]
>  アセンブリ参照の `Embed Interop Types` プロパティを `True` に設定することは、コマンド ライン コンパイラの `/link` オプションを使用してアセンブリを参照することと同じです。  
  
 **エラー ID:** BC40059  
  
### <a name="to-address-this-warning"></a>この警告に対処するには  
  
-   両方のアセンブリに相互運用の型情報を埋め込むには、assembly1 へのすべての参照の `Embed Interop Types` プロパティを `True` に設定します。  
  
-   assembly1 の `Embed Interop Types` プロパティを `False` に設定すると警告を回避できます。 この場合は、相互運用機能型の情報は、プライマリ相互運用機能アセンブリ (PIA) によって提供されます。  
  
## <a name="see-also"></a>関連項目

- [/link (Visual Basic)](../../../visual-basic/reference/command-line-compiler/link.md)
- [アンマネージ コードとの相互運用](../../../framework/interop/index.md)
