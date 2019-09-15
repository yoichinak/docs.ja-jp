---
title: '方法: イメージ メタデータを読み取る'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- metadata [Windows Forms], property item
- metadata [Windows Forms], reading image
ms.assetid: 72ec0b31-0be7-444a-9575-1dbcb864e0be
ms.openlocfilehash: 8294bc6596c408160a50d9d7d5e6154f66025c73
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/14/2019
ms.locfileid: "70988570"
---
# <a name="how-to-read-image-metadata"></a>方法: イメージ メタデータを読み取る
一部のイメージファイルには、イメージの機能を確認するために読み取ることができるメタデータが含まれています。 たとえば、デジタル写真には、イメージのキャプチャに使用されるカメラのメーカーとモデルを決定するために読み取ることができるメタデータが含まれている場合があります。 GDI + を使用すると、既存のメタデータを読み取ることができます。また、イメージファイルに新しいメタデータを書き込むこともできます。  
  
 Gdi + は、 <xref:System.Drawing.Imaging.PropertyItem>オブジェクトに個々のメタデータを格納します。 オブジェクトのプロパティ<xref:System.Drawing.Image.PropertyItems%2A>を読み取って、ファイルからすべてのメタデータを取得できます。 <xref:System.Drawing.Image> プロパティ<xref:System.Drawing.Image.PropertyItems%2A>は、オブジェクトの<xref:System.Drawing.Imaging.PropertyItem>配列を返します。  
  
 <xref:System.Drawing.Imaging.PropertyItem>オブジェクトには`Id`、 `Value` 、、`Type`、およびの4つのプロパティがあります。 `Len`  
  
## <a name="id"></a>Id  
 メタデータ項目を識別するタグ。 次の表に、に<xref:System.Drawing.Imaging.PropertyItem.Id%2A>割り当てることができる値をいくつか示します。  
  
|16進数値|説明|  
|-----------------------|-----------------|  
|0x0320<br /><br /> 0x010F<br /><br /> 0x0110<br /><br /> 0x9003<br /><br /> 0x829A<br /><br /> 0x5090<br /><br /> 0x5091|イメージのタイトル<br /><br /> 装置の製造元<br /><br /> 装置モデル<br /><br /> ExifDTOriginal<br /><br /> Exif 公開時間<br /><br /> 輝度テーブル<br /><br /> クロミナンステーブル|  
  
## <a name="value"></a>値  
 値の配列。 値の形式は、 <xref:System.Drawing.Imaging.PropertyItem.Type%2A>プロパティによって決まります。  
  
## <a name="len"></a>Len  
 プロパティが<xref:System.Drawing.Imaging.PropertyItem.Value%2A>指す値の配列の長さ (バイト単位)。  
  
## <a name="type"></a>種類  
 プロパティが`Value`指す配列内の値のデータ型。 次の表に、 `Type`プロパティ値によって示される形式を示します。  
  
|数値|説明|  
|-------------------|-----------------|  
|1|`Byte`。|  
|2|ASCII とし`Byte`てエンコードされたオブジェクトの配列|  
|3|16ビット整数|  
|4|32ビット整数|  
|5|有理数を表す 2 `Byte`つのオブジェクトの配列|  
|6|使用しない|  
|7|未定義|  
|8|使用しない|  
|9|`SLong`|  
|10|`SRational`|  
  
## <a name="example"></a>例  
  
### <a name="description"></a>説明  
 次のコード例では、ファイル`FakePhoto.jpg`内の7つのメタデータを読み取り、表示します。 リスト内の2番目の (インデックス 1) プロパティ<xref:System.Drawing.Imaging.PropertyItem.Id%2A>項目には、0x010F ( <xref:System.Drawing.Imaging.PropertyItem.Type%2A>装置の製造元) と 2 (ASCII エンコードされたバイト配列) があります。 このコード例では、そのプロパティ項目の値を表示します。  
  
 このコードでは、次のような出力が生成されます。  
 
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
  
### <a name="code"></a>コード  
 [!code-csharp[System.Drawing.WorkingWithImages#51](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#51)]
 [!code-vb[System.Drawing.WorkingWithImages#51](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#51)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 前の例は、Windows フォームで使用するために設計されていて、<xref:System.Windows.Forms.Control.Paint> イベント ハンドラーのパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` を必要とします。 フォームの<xref:System.Windows.Forms.Control.Paint>イベントを処理し、このコードを描画イベントハンドラーに貼り付けます。 をシステム上`FakePhoto.jpg`で有効なイメージ名とパスに置き換えて、 `System.Drawing.Imaging`名前空間をインポートする必要があります。  
  
## <a name="see-also"></a>関連項目

- [イメージ、ビットマップ、メタファイル](images-bitmaps-and-metafiles.md)
- [イメージ、ビットマップ、アイコン、およびメタファイルの操作](working-with-images-bitmaps-icons-and-metafiles.md)
