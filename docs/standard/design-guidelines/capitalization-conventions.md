---
title: 大文字の使用規則
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- camel-case names [.NET Framework]
- class library design guidelines [.NET Framework], capitalization
- Pascal-case names [.NET Framework]
- case sensitivity, capitalization conventions
- names [.NET Framework], capitalization
ms.assetid: 4c4ea526-9203-486f-b72d-29d61c5b3c6d
author: KrzysztofCwalina
ms.openlocfilehash: e0da4cd747846921d170d9c07d6f1fb91dbd4ed7
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64615248"
---
# <a name="capitalization-conventions"></a>大文字の使用規則
この章のレイアウトを使用するための単純なメソッドのガイドラインは、型、メンバー、およびパラメーターを読みやすくする識別子を一貫した適用されるときに場合です。  
  
## <a name="capitalization-rules-for-identifiers"></a>識別子の大文字と小文字の規則  
 識別子内の単語を区別するためには、識別子内の各単語の最初の文字を大文字に変換します。 アンダー スコアは、単語を区別するために使用しないでくださいまたはさらに言えば、識別子で任意の場所。 識別子の使用によって、識別子を大文字に変換する 2 つの適切な方法はあります。  
  
- Pascal 表記を使用  
  
- キャメル ケース  
  
 Pascal 表記を使用規則は、パラメーター名を除くすべての識別子には、次の例に示すように、(2 文字の長さを頭字語を含む) の各単語の最初の文字を大文字になります。  
  
 `PropertyDescriptor`  
 `HtmlTag`  
  
 特殊なケースは、次の識別子で示すように 2 文字の頭字語が両方の文字が大文字で入力に行われます。  
  
 `IOStream`  
  
 キャメル ケース規約、パラメーター名では、専用に使用では、次の例に示すように、最初の単語以外の各単語の最初の文字が大文字にします。 例に示すも camel 形式の識別子を開始 2 文字の頭字語は小文字の両方です。  
  
 `propertyDescriptor`  
 `ioStream`  
 `htmlTag`  
  
 **✓ DO** すべてパブリック メンバー、種類、および名前空間の名前を複数の単語で構成される pascal 表記を使用を使用します。  
  
 **✓ DO** パラメーター名の camel 表記を使用します。  
  
 次の表では、さまざまな種類の識別子の大文字と小文字の規則について説明します。  
  
|識別子|大文字小文字の区別|例|  
|----------------|------------|-------------|  
|名前空間|Pascal 形式|`namespace System.Security { ... }`|  
|型|Pascal 形式|`public class StreamReader { ... }`|  
|Interface|Pascal 形式|`public interface IEnumerable { ... }`|  
|メソッド|Pascal 形式|`public class Object {` <br />  `public virtual string ToString();` <br /> `}`|  
|プロパティ|Pascal 形式|`public class String {` <br />  `public int Length { get; }` <br /> `}`|  
|イベント|Pascal 形式|`public class Process {` <br />  `public event EventHandler Exited;` <br /> `}`|  
|フィールド|Pascal 形式|`public class MessageQueue {` <br />  `public static readonly TimeSpan` <br /> `InfiniteTimeout;` <br /> `}` <br /> `public struct UInt32 {` <br />  `public const Min = 0;` <br /> `}`|  
|列挙値|Pascal 形式|`public enum FileMode {` <br />  `Append,` <br />  `...` <br /> `}`|  
|パラメーター|Camel 形式|`public class Convert {` <br />  `public static int ToInt32(string value);` <br /> `}`|  
  
## <a name="capitalizing-compound-words-and-common-terms"></a>複合語の大文字と一般的な用語  
 ほとんどの複合語は、大文字と小文字の目的で 1 つの単語として扱われます。  
  
 **X DO NOT** いわゆる閉じたフォームの複合語内の各単語を大文字に変換します。  
  
 これらは、複合語のエンドポイントなど、1 つの単語として書き込まれます。 大文字と小文字のガイドラインについては、目的には、1 つの単語として閉じられたフォームの複合語を処理します。 現在のディクショナリを使用すると、複合語が閉じたフォームで記述されたかどうかを判断できます。  
  
|Pascal 形式|Camel 形式|Not|  
|------------|-----------|---------|  
|`BitFlag`|`bitFlag`|`Bitflag`|  
|`Callback`|`callback`|`CallBack`|  
|`Canceled`|`canceled`|`Cancelled`|  
|`DoNot`|`doNot`|`Don't`|  
|`Email`|`email`|`EMail`|  
|`Endpoint`|`endpoint`|`EndPoint`|  
|`FileName`|`fileName`|`Filename`|  
|`Gridline`|`gridline`|`GridLine`|  
|`Hashtable`|`hashtable`|`HashTable`|  
|`Id`|`id`|`ID`|  
|`Indexes`|`indexes`|`Indices`|  
|`LogOff`|`logOff`|`LogOut`|  
|`LogOn`|`logOn`|`LogIn`|  
|`Metadata`|`metadata`|`MetaData, metaData`|  
|`Multipanel`|`multipanel`|`MultiPanel`|  
|`Multiview`|`multiview`|`MultiView`|  
|`Namespace`|`namespace`|`NameSpace`|  
|`Ok`|`ok`|`OK`|  
|`Pi`|`pi`|`PI`|  
|`Placeholder`|`placeholder`|`PlaceHolder`|  
|`SignIn`|`signIn`|`SignOn`|  
|`SignOut`|`signOut`|`SignOff`|  
|`UserName`|`userName`|`Username`|  
|`WhiteSpace`|`whiteSpace`|`Whitespace`|  
|`Writable`|`writable`|`Writeable`|  
  
## <a name="case-sensitivity"></a>大文字と小文字の区別  
 CLR で実行できる言語は、いくつかの操作を行いますが、大文字小文字の区別をサポートする必要はありません。 お使いの言語をサポートしている場合でも、フレームワークにアクセスする他の言語は必要ありません。 したがって、外部からアクセス可能であるすべての Api は、場合、同じコンテキストで 2 つの名前を区別するために単独で使用できません。  
  
 **X DO NOT** すべてのプログラミング言語が大文字小文字を区別があると仮定します。 しかし、そうではありません。 大文字と小文字だけ名前が異なることはできません。  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 *Pearson Education, Inc. からのアクセス許可によって了承を得て転載[Framework デザイン ガイドライン。規則、手法、および再利用可能な .NET ライブラリの第 2 版のパターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina、Brad 内容では、Microsoft Windows の開発シリーズの一部として、Addison-wesley Professional、2008 年 10 月 22日を公開します。*  
  
## <a name="see-also"></a>関連項目

- [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)
- [名前付けのガイドライン](../../../docs/standard/design-guidelines/naming-guidelines.md)
