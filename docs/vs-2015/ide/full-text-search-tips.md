---
title: Tam metin arama ipuçları | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- hv_search
helpviewer_keywords:
- Help Viewer 2.0, full-text search tips
- full-text search tips [Help Viewer 2.0]
ms.assetid: bcaad23d-2ca7-4bec-8b54-b884bc34e70b
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 85770dfd3c610f92bcb190b7a2c151b40cd31a4c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49850054"
---
# <a name="full-text-search-tips"></a>Tam Metin Araması İpuçları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Konumlama bilgileri Yardım için daha kullanışlı yöntemler tam metin araması gerçekleştirerek biridir. İyileştirmek ve sonuçlarınızı özelleştirmek için söz dizimi sorgunuzu nasıl etkilediğini anlamanız gerekir. Bu konu, sorgularınızı ipuçları, yordamlar ve kolaylaştırıyor daha iyi yardımcı olacak ayrıntılı sözdizimi bilgiler sağlar.  
  
## <a name="full-text-search-tips"></a>Tam Metin Araması İpuçları  
 Yalnızca bu konular, biçimlendirme Yardım nasıl yorumlayacağını anlarsanız, kullandığınız ilgilendiği sorgularda dönün. daha fazla hedeflenen aramaları oluşturabilirsiniz. Bu, özel karakterler, ayrılmış sözcükleri ve filtreleri biçimler.  
  
### <a name="general-guidelines"></a>Genel Yönergeler  
 Aşağıdaki tabloda, bazı temel kurallara ve arama sorguları Yardımı'nda geliştirmeye yönelik yönergeleri içerir.  
  
|Sözdizimi|Açıklama|  
|------------|-----------------|  
|Büyük/küçük harfe duyarlılık|Aramalar büyük küçük harfe duyarlı değildir. Büyük veya küçük harf karakterler kullanarak arama ölçütlerinizi geliştirin. Örneğin, "OLE" ve "ole" aynı sonuçları döndürür.|  
|Karakter birleşimleri|Yalnızca bireysel harfler için (a – z) arama yapılamıyor veya sayılar (0 – 9). Aktarmaya çalışırsanız arama belirli gibi "ve", "Kimden" sözcükler ayrılmıştır ve "ile", bunlar yoksayılır. Daha fazla bilgi için "bu konunun ilerleyen bölümlerinde alan" (durdurma sözcükleri) aramalarındaki yoksayıldı sözcükler.|  
|Değerlendirme sırası|Arama sorguları soldan sağa doğru değerlendirilir.|  
  
### <a name="search-syntax"></a>Arama söz dizimi  
 Bu dize, "sözcük1 sözcük2" gibi birden çok sözcük içeren bir arama dizesi belirtirseniz yazmakla eşdeğerdir: "sözcük1 sözcük2 ve", tüm arama dizesindeki kelimeler içeren konuların döndürür.  
  
> [!IMPORTANT]
> 1. Deyim aramaları desteklenmiyor. Arama dizesinde birden fazla belirtmeniz durumunda döndürülen konuları tüm belirttiğiniz sözcükleri ancak mutlaka belirttiğiniz terimin içerir.  
>    2.  Mantıksal işleçler, Boole sözcükler arasındaki ilişki belirtmek için kullanın. AND, OR, NOT, gibi mantıksal işleçler içerir ve yakında, daha fazla için aramanızı daraltın. Örneğin, "UNION bildirmek için" arama yaparsanız, arama sonuçlarını sözcükler "bildirim" ve "birleşim" en fazla birkaç sözcük birbirlerinden içeren konuları içerir. Daha fazla bilgi için [arama ifadelerindeki mantıksal işleçler](../ide/logical-operators-in-search-expressions.md).  
  
### <a name="filters"></a>FilTReleri  
 Gelişmiş arama işleçleri kullanarak, arama sonuçlarını daha fazla kısıtlayabilirsiniz. Yardımı, tam metin arama sonuçlarını filtrelemek için kullanabileceğiniz üç kategorileri içerir: Başlık, kod ve anahtar sözcüğü. Daha fazla bilgi için [arama ifadelerindeki Gelişmiş arama işleçleri](../ide/advanced-search-operators-in-search-expressions.md).  
  
### <a name="ranking-of-search-results"></a>Arama Sonuçları sıralama  
 Arama algoritması derece yardımcı olmak için belirli ölçütleri geçerli arama sonuçları daha yüksek veya düşük sonuçlar listesinde. Genel olarak:  
  
1.  Başlık arama sözcükleri içeren içerikleri olmayan içerik daha yüksek önem derecesi.  
  
2.  Arama sözcükleri yakınında içeren içerik olmayan içerik daha yüksek önem derecesi.  
  
3.  Daha yüksek yoğunlukta arama sözcükleri içeren içeriği daha düşük bir arama sözcükleri yoğunluğu olan içeriği, daha yüksek önem derecesi.  
  
### <a name="words-ignored-in-searches-stop-words"></a>Sözcük aramaları (durdurma sözcükleri) yoksayıldı  
 Yaygın olarak karşılaşılan bir sözcük veya durdurma sözcükleri bazen verilen sayılar, otomatik olarak bir tam metin araması sırasında yok sayılır. İfade "geçiş" için arama yaparsanız, örneğin, arama sonuçlarını "geçiş" sözcüğünü içeren konuların değil "ile ancak" görüntüler.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bilgi bulun](../ide/locate-information.md)   
 [Arama İfadelerindeki Mantıksal İşleçler](../ide/logical-operators-in-search-expressions.md)



