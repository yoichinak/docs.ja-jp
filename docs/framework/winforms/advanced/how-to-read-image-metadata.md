---
title: '方法 : イメージ メタデータを読み取る'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- metadata [Windows Forms], property item
- metadata [Windows Forms], reading image
ms.assetid: 72ec0b31-0be7-444a-9575-1dbcb864e0be
ms.openlocfilehash: e2b56175e625281a920c390e5feb4238e3cb7f44
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182515"
---
# <a name="how-to-read-image-metadata"></a>方法 : イメージ メタデータを読み取る

一部のイメージ ファイルには、イメージの機能を特定するために読み取ることができるメタデータが含まれています。 たとえば、デジタル写真には、画像のキャプチャに使用するカメラのモデルとモデルを決定するために読み取ることができるメタデータが含まれている場合があります。 GDI+ を使用すると、既存のメタデータを読み取ることができ、新しいメタデータをイメージ ファイルに書き込むこともできます。

GDI+ は、オブジェクト内の個々のメタデータ<xref:System.Drawing.Imaging.PropertyItem>を格納します。 オブジェクトのプロパティを<xref:System.Drawing.Image.PropertyItems%2A>読み取<xref:System.Drawing.Image>って、ファイルからすべてのメタデータを取得できます。 この<xref:System.Drawing.Image.PropertyItems%2A>プロパティは、オブジェクトの<xref:System.Drawing.Imaging.PropertyItem>配列を返します。

オブジェクト<xref:System.Drawing.Imaging.PropertyItem>には、 、 、 `Id`、 `Value` `Len`、`Type`の 4 つのプロパティがあります。

## <a name="id"></a>Id

メタデータ項目を識別するタグ。 割り当て可能な値<xref:System.Drawing.Imaging.PropertyItem.Id%2A>の一部を次の表に示します。

|16 進数値|説明|
|-----------------------|-----------------|
|0x0320<br /><br /> 0x010F<br /><br /> 0x0110<br /><br /> 0x9003<br /><br /> 0x829A<br /><br /> 0x5090<br /><br /> 0x5091|画像タイトル<br /><br /> 機器メーカー<br /><br /> 機器モデル<br /><br /> エクシフトオリジナル<br /><br /> Exif 露出時間<br /><br /> 輝度テーブル<br /><br /> クロミナンステーブル|

## <a name="value"></a>Value

値の配列です。 値の形式は<xref:System.Drawing.Imaging.PropertyItem.Type%2A>、プロパティによって決まります。

## <a name="len"></a>Len

<xref:System.Drawing.Imaging.PropertyItem.Value%2A>プロパティが指す値の配列の長さ (バイト単位)。

## <a name="type"></a>Type

プロパティが指す配列内の値の`Value`データ型。 プロパティ値で示される`Type`形式を次の表に示します。

|数値|説明|
|-------------------|-----------------|
|1|`Byte` 変数|
|2|ASCII として`Byte`エンコードされたオブジェクトの配列|
|3|16 ビット整数|
|4|32 ビット整数|
|5|有理数を`Byte`表す 2 つのオブジェクトの配列|
|6|使用されていない|
|7|未定義。|
|8|使用されていない|
|9|`SLong`|
|10|`SRational`|

## <a name="example"></a>例
  
次のコード例では、ファイル内の 7 つのメタデータを読`FakePhoto.jpg`み取り、表示します。 リストの 2 番目の (インデックス 1) プロパティ項目は、0x010F (機器メーカー) と<xref:System.Drawing.Imaging.PropertyItem.Id%2A><xref:System.Drawing.Imaging.PropertyItem.Type%2A>2 (ASCII エンコードバイト配列) を持ちます。 このコード例では、そのプロパティ項目の値を表示します。

[!code-csharp[System.Drawing.WorkingWithImages#51](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#51)]
[!code-vb[System.Drawing.WorkingWithImages#51](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#51)]

このコードは、次のような出力を生成します。

```output
 Property Item 0
  
 id: 0x320
  
 type: 2

 length: 16 bytes
  
 Property Item 1
  
 id: 0x10f
  
 type: 2
  
 length: 17 bytes
  
 Property Item 2
  
 id: 0x110
  
 type: 2
  
 length: 7 bytes
  
 Property Item 3
  
 id: 0x9003
  
 type: 2
  
 length: 20 bytes
  
 Property Item 4
  
 id: 0x829a
  
 type: 5
  
 length: 8 bytes
  
 Property Item 5
  
 id: 0x5090
  
 type: 3
  
 length: 128 bytes
  
 Property Item 6
  
 id: 0x5091
  
 type: 3
  
 length: 128 bytes
  
 The equipment make is Northwind Camera.
 ```

## <a name="compiling-the-code"></a>コードのコンパイル

上記の例は Windows フォームで使用するように設計されており、<xref:System.Windows.Forms.PaintEventArgs>`e`<xref:System.Windows.Forms.Control.Paint>イベント ハンドラーのパラメーターである が必要です。 フォームの<xref:System.Windows.Forms.Control.Paint>イベントを処理し、このコードを paint イベント ハンドラーに貼り付けます。 システムで有効`FakePhoto.jpg`なイメージ名とパスで置き換え、名前空間を`System.Drawing.Imaging`インポートする必要があります。

## <a name="see-also"></a>関連項目

- [イメージ、ビットマップ、およびメタファイル](images-bitmaps-and-metafiles.md)
- [イメージ、ビットマップ、アイコン、およびメタファイルの操作](working-with-images-bitmaps-icons-and-metafiles.md)
