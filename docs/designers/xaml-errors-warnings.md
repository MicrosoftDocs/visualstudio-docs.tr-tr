---
title: XAML hataları ve Uyarıları
ms.date: 03/06/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 34eac8a0-7ec5-4c40-b97a-0126ed367931
author: karann-msft
ms.author: karann
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 09251f13cafa320e2736e9c61135283bb9e9739d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49844191"
---
# <a name="xaml-errors-and-warnings"></a>XAML hataları ve uyarıları

XAML yazarken, yazdığınız sırada Visual Studio kod analiz eder. Bir hata algılandığında bir dalgalı bir kod satırı görünür. Dalgalı çizgi geldiğinizde, hata veya uyarı hakkında daha fazla bilgi sağlar. Bazı hatalar ve Uyarılar için hızlı eylem ampul görüntülenir ve kullanarak **Ctrl**+**.** klavye kısayolu, sorunu düzeltmek için seçenekleri görüntüler.

## <a name="error-types"></a>Hata türleri

Arka planda birden çok araç, XAML paralel analiz edin. XAML hataları, hatanın algılandığı araca bağlı aşağıdaki üç türlerden birinde ayrılır:

|**Tarafından algılanan hata**|**Hata kodu biçimi**|
| - |-----------------|
|XAML dil hizmeti (XAML Düzenleyicisi)|XLSxxxx|
|XAML Tasarımcısı|XDGxxxx|
|XAML Düzenle ve devam et|XECxxxx|

> [!Note]
> Tüm hata veya uyarı karşılık gelen bir kod vardır. Bu hatalar genellikle XAML Tasarımcısı hatalardır.


## <a name="suppress-xaml-designer-errors"></a>XAML Tasarımcısı Hataları Gizle

Açık **seçenekleri** seçerek iletişim **Araçlar > Seçenekler**ve ardından **metin düzenleyicisi > XAML > çeşitli**.

Onay kutusunu temizleyin **XAML tasarımcısı tarafından algılanan hataları göster** onay kutusu.

![XAML Tasarımcısı Hataları Gizle](../designers/media/suppress_xaml_designer_errors.png)


