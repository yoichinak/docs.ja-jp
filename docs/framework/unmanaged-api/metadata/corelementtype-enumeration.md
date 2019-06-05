---
title: CorElementType Enumeration1
ms.date: 03/30/2017
api_name:
- CorElementType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorElementType
helpviewer_keywords:
- CorElementType enumeration [.NET Framework metadata]
ms.assetid: c3809c8f-1737-4f0f-9442-0c01ee689871
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 48650a85a88f36cd51adb1bbec0436fb5d75ecfb
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2019
ms.locfileid: "66690368"
---
# <a name="corelementtype-enumeration1"></a>CorElementType Enumeration1

共通言語ランタイムを指定します<xref:System.Type>、型修飾子、またはメタデータの型シグネチャの種類に関する情報。

## <a name="syntax"></a>構文

```
typedef enum CorElementType {
    ELEMENT_TYPE_END            = 0x0,
    ELEMENT_TYPE_VOID           = 0x1,
    ELEMENT_TYPE_BOOLEAN        = 0x2,
    ELEMENT_TYPE_CHAR           = 0x3,
    ELEMENT_TYPE_I1             = 0x4,
    ELEMENT_TYPE_U1             = 0x5,
    ELEMENT_TYPE_I2             = 0x6,
    ELEMENT_TYPE_U2             = 0x7,
    ELEMENT_TYPE_I4             = 0x8,
    ELEMENT_TYPE_U4             = 0x9,
    ELEMENT_TYPE_I8             = 0xa,
    ELEMENT_TYPE_U8             = 0xb,
    ELEMENT_TYPE_R4             = 0xc,
    ELEMENT_TYPE_R8             = 0xd,
    ELEMENT_TYPE_STRING         = 0xe,

    ELEMENT_TYPE_PTR            = 0xf,
    ELEMENT_TYPE_BYREF          = 0x10,

    ELEMENT_TYPE_VALUETYPE      = 0x11,
    ELEMENT_TYPE_CLASS          = 0x12,
    ELEMENT_TYPE_VAR            = 0x13,
    ELEMENT_TYPE_ARRAY          = 0x14,
    ELEMENT_TYPE_GENERICINST    = 0x15,
    ELEMENT_TYPE_TYPEDBYREF     = 0x16,

    ELEMENT_TYPE_I              = 0x18,
    ELEMENT_TYPE_U              = 0x19,
    ELEMENT_TYPE_FNPTR          = 0x1B,
    ELEMENT_TYPE_OBJECT         = 0x1C,
    ELEMENT_TYPE_SZARRAY        = 0x1D,
    ELEMENT_TYPE_MVAR           = 0x1e,

    ELEMENT_TYPE_CMOD_REQD      = 0x1F,
    ELEMENT_TYPE_CMOD_OPT       = 0x20,

    ELEMENT_TYPE_INTERNAL       = 0x21,
    ELEMENT_TYPE_MAX            = 0x22,

    ELEMENT_TYPE_MODIFIER       = 0x40,
    ELEMENT_TYPE_SENTINEL       = 0x01 | ELEMENT_TYPE_MODIFIER,
    ELEMENT_TYPE_PINNED         = 0x05 | ELEMENT_TYPE_MODIFIER

} CorElementType;
```

## <a name="members"></a>メンバー

|メンバー|説明|
|------------|-----------------|
|`ELEMENT_TYPE_END`|内部的に使用します。|
|`ELEMENT_TYPE_VOID`|Void 型。|
|`ELEMENT_TYPE_BOOLEAN`|ブール型|
|`ELEMENT_TYPE_CHAR`|文字型。|
|`ELEMENT_TYPE_I1`|1 バイトの符号付き整数では。|
|`ELEMENT_TYPE_U1`|1 バイトの符号なし整数。|
|`ELEMENT_TYPE_I2`|符号付きの 2 バイト整数。|
|`ELEMENT_TYPE_U2`|2 バイトの符号なし整数。|
|`ELEMENT_TYPE_I4`|符号付きの 4 バイト整数。|
|`ELEMENT_TYPE_U4`|4 バイトの符号なし整数。|
|`ELEMENT_TYPE_I8`|符号付き 8 バイト整数。|
|`ELEMENT_TYPE_U8`|8 バイトの符号なし整数。|
|`ELEMENT_TYPE_R4`|4 バイト浮動小数点。|
|`ELEMENT_TYPE_R8`|8 バイト浮動小数点。|
|`ELEMENT_TYPE_STRING`|System.String 型。|
|`ELEMENT_TYPE_PTR`|ポインター型の修飾子。|
|`ELEMENT_TYPE_BYREF`|参照型の修飾子。|
|`ELEMENT_TYPE_VALUETYPE`|値の型修飾子です。|
|`ELEMENT_TYPE_CLASS`|クラス型の修飾子。|
|`ELEMENT_TYPE_VAR`|クラスの変数の型修飾子です。|
|`ELEMENT_TYPE_ARRAY`|多次元配列の型修飾子です。|
|`ELEMENT_TYPE_GENERICINST`|ジェネリック型の型修飾子です。|
|`ELEMENT_TYPE_TYPEDBYREF`|型指定された参照。|
|`ELEMENT_TYPE_I`|ネイティブの整数のサイズ。|
|`ELEMENT_TYPE_U`|符号なしネイティブ整数のサイズ。|
|`ELEMENT_TYPE_FNPTR`|関数へのポインター。|
|`ELEMENT_TYPE_OBJECT`|System.Object 型。|
|`ELEMENT_TYPE_SZARRAY`|1 次元、0 の配列の下限の型修飾子です。|
|`ELEMENT_TYPE_MVAR`|メソッドの変数の型修飾子です。|
|`ELEMENT_TYPE_CMOD_REQD`|C 言語には、修飾子が必要です。|
|`ELEMENT_TYPE_CMOD_OPT`|C 言語の省略可能な修飾子。|
|`ELEMENT_TYPE_INTERNAL`|内部的に使用します。|
|`ELEMENT_TYPE_MAX`|無効な型。|
|`ELEMENT_TYPE_MODIFIER`|内部的に使用します。|
|`ELEMENT_TYPE_SENTINEL`|Sentinel 可変個のパラメーターの一覧については、型修飾子です。|
|`ELEMENT_TYPE_PINNED`|内部的に使用します。|

## <a name="remarks"></a>Remarks

型修飾子より複雑な型を表すための基礎を形成します。 A`CorElementType`型修飾子の値が値型シグネチャ内直後に適用されます。 次の値、`CorElementType`型修飾子の値を指定できます、`CorElementType`単純型の値、メタデータ トークン、または次の表で指定されているその他の値。

> [!NOTE]
> すべての数値 (*数*、*引数カウント*、*メタデータ トークン*、*ランク*、*カウント*、および*バインド*) 圧縮された整数として格納されます。 参照してください[標準 ECMA 335 の共通言語基盤 (CLI)](https://go.microsoft.com/fwlink/?LinkID=116487)詳細については、ECMA の Web サイト。

|型修飾子|Format|
|-------------------|------------|
|`ELEMENT_TYPE_PTR`|ELEMENT_TYPE_PTR \<a `CorElementType` value>|
|`ELEMENT_TYPE_BYREF`|ELEMENT_TYPE_BYREF \<a `CorElementType` value>|
|`ELEMENT_TYPE_VALUETYPE`|ELEMENT_TYPE_VALUETYPE \<、`mdTypeDef`メタデータ トークン >|
|`ELEMENT_TYPE_CLASS`|ELEMENT_TYPE_CLASS \<、`mdTypeDef`メタデータ トークン >|
|`ELEMENT_TYPE_VAR`|ELEMENT_TYPE_VAR \<number>|
|`ELEMENT_TYPE_ARRAY`|ELEMENT_TYPE_ARRAY \<a `CorElementType` value> \<rank> \<count1> \<bound1> ... \<countN> \<boundN>|
|`ELEMENT_TYPE_GENERICINST`|ELEMENT_TYPE_GENERICINST \<、`mdTypeDef`メタデータ トークン >\<引数カウント > \<arg1 >.\<argN >|
|`ELEMENT_TYPE_FNPTR`|Typ ELEMENT_TYPE_FNPTR\<には関数の呼び出し規約を含む完全なシグネチャ >|
|`ELEMENT_TYPE_SZARRAY`|ELEMENT_TYPE_SZARRAY \<、`CorElementType`値 >|
|`ELEMENT_TYPE_MVAR`|ELEMENT_TYPE_MVAR \<number>|
|`ELEMENT_TYPE_CMOD_REQD`|ELEMENT_TYPE_\<、`mdTypeRef`または`mdTypeDef`メタデータ トークン >|
|`ELEMENT_TYPE_CMOD_OPT`|E_T_CMOD_OPT \<、`mdTypeRef`または`mdTypeDef`メタデータ トークン >|

## <a name="requirements"></a>必要条件

**プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。

**ヘッダー:** CorHdr.h

**.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

## <a name="see-also"></a>関連項目

- [メタデータ列挙型](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
