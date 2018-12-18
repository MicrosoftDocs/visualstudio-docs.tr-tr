---
title: Biçim belirleyiciler C# | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
- CSharp
helpviewer_keywords:
- expressions [C#], formatting values
- variables [debugger], watch variable symbols
- symbols, watch variable formatting
- QuickWatch dialog box, using format specifiers
- specifiers, watch variable format
- QuickWatch dialog box, format specifiers in C#
- specifiers
- watch variable symbols
- Watch window, format specifiers in C#
- format specifiers, debugger
- debugger, format specifiers recognized by
ms.assetid: 345c8589-5f36-4d34-a58c-e56271687dd6
caps.latest.revision: 34
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 330a32b20eeab172ebf36e49f16e79aa936a1bdc
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51754162"
---
# <a name="format-specifiers-in-c"></a>C# içindeki Biçim Belirticileri #
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

İçinde bir değer görüntülenir biçimini değiştirebilirsiniz **Watch** penceresi biçim belirticilerini kullanma. İçindeki Biçim belirticileri kullanabilirsiniz **hemen** penceresinde **komut** penceresinde ve hatta kaynak pencerelerinde. Bu pencereler içinde bir ifade üzerinde duraklarsanız, sonuç DataTip içinde görünür. DataTips, DataTip görünümü içinde biçim belirticisini yansıtır.  
  
 Bir biçim belirtici kullanmak için bir virgül ve ifade yazın. Virgülden sonra uygun Belirleyicisi ekleyin.  
  
## <a name="using-format-specifiers"></a>Biçim belirticilerini kullanma  
 Aşağıdaki koda sahipseniz:  
  
```  
{  
        int my_var1 = 0x0065;  
        int my_var2 = 0x0066;  
        int my_var3 = 0x0067;  
}  
```  
  
 Ekleme `my_var1` İzleme penceresinde değişkenini (hata ayıklarken, **hata ayıklama / Windows / izleyin / izleyin 1**) ve görüntü onaltılığa ayarlayın (içinde **izleme** penceresinde, değişkeni sağ tıklatın ve seçin **Onaltılık gösterim**). Artık **Watch** penceresi 0x0065 değeri içerdiğini gösterir. Bkz. Bu değer bir ondalık tamsayı Ad sütununda bir onaltılık tamsayı yerine değişken adından sonra ifade ondalık biçim belirteci eklemek için: **, d**. Değer sütunu artık ondalık değeri 101 görüntüler  
  
 ![WatchFormatCSharp](../debugger/media/watchformatcsharp.png "WatchFormatCSharp")  
  
## <a name="format-specifiers"></a>Biçim belirticileri  
 Aşağıdaki tablo, hata ayıklayıcı tarafından tanınan C# biçim belirteçlerini gösterir.  
  
|Belirleyici|Biçimi|Özgün izleme değeri|Görüntüler|  
|---------------|------------|--------------------------|--------------|  
|AC|Bir ifadenin değerlendirmesine zorlar. Örtülü değerlendirme özellikleri ve örtük işlev çağrılarını devre dışı bırakıldığında bu yararlı olabilir. Bkz: [yan etkiler ve ifadeler](http://msdn.microsoft.com/library/e1f8a6ea-9e19-481d-b6bd-df120ad3bf4e).|"Kapalı işlev değerlendirme kullanıcı tarafından devre dışı" iletisi|\<Değer >|  
|d|Ondalık tamsayı|0x0065|101|  
|dinamik|Dinamik bir görünümü kullanarak belirtilen nesneyi görüntüler|Dinamik görünüm dahil olmak üzere nesnenin tüm üyelerini görüntüler|Yalnızca dinamik görünüm görüntüler|  
|h|Onaltılık tamsayı|61541|0x0000F065|  
|Nq|hiçbir tırnak işaretleri dize|"Benim dize"|My dize|  
|gizli|Tüm genel ve genel olmayan üyeleri görüntüler|Görüntüler Genel üyeler|Tüm üyelerini görüntüler|  
|Ham|Ham madde düğümüne göründüğü gibi öğesi görüntüler. Proxy nesneleri yalnızca geçerli.|Sözlük\<T >|Sözlük işlenmemiş bir görünümünü\<T >|  
|sonuçlar|IEnumerable veya IEnumerable uygulayan bir tür değişkeninin ile kullanılan\<T >, genellikle bir sorgu ifadesinin sonucu. Sorgu sonucu içeren üyelerini görüntüler.|Tüm üyelerini görüntüler.|Üyeleri karşılamak görüntüler sorgunun koşulları.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzleme ve QuickWatch Windows](../debugger/watch-and-quickwatch-windows.md)   
 [Değişken Windows](http://msdn.microsoft.com/library/ce0a67f6-2502-4b7a-ba45-cc32f8aeba3e)





