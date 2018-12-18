---
title: Değer (XAttribute dinamik özelliği)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: reference
apiname:
- XAttribute.Value
apitype: Assembly
ms.assetid: 019733d2-e050-4120-b537-831cd3fc008e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 473ff5b0124a050b60c9dc02929b2bad83f3661e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49842349"
---
# <a name="value-xattribute-dynamic-property"></a>Değer (XAttribute dinamik özelliği)

Alır veya XML öznitelik değerini ayarlar.

## <a name="syntax"></a>Sözdizimi

```xaml
attrib.Value
```

## <a name="property-valuereturn-value"></a>Özellik değeri/dönüş değeri

A <xref:System.String> içeren bu özniteliğin değeri.

## <a name="exceptions"></a>Özel Durumlar

|Özel durum türü|Koşul|
| - |---------------|
|<xref:System.ArgumentNullException>|Ayarlarken `value` olduğu `null`.|

## <a name="remarks"></a>Açıklamalar

Bu özellik değerine eşdeğer olan <xref:System.Xml.Linq.XAttribute.Value%2A> özelliği <xref:System.Xml.Linq.XAttribute?displayProperty=fullName> sınıfı, ancak bu dinamik özellik de değişiklik bildirimleri destekler.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=fullName>
- [XAttribute sınıfı dinamik özellikleri](../designers/xattribute-class-dynamic-properties.md)
- [Öznitelik](../designers/attribute-xelement-dynamic-property.md)