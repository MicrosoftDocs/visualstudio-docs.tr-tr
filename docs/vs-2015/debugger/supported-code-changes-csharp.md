---
title: Desteklenen kod değişiklikleri (C#) | Microsoft Docs
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
helpviewer_keywords:
- Edit and Continue [C#], supported code changes
ms.assetid: c7a48ea9-5a7f-4328-a9d7-f0e76fac399d
caps.latest.revision: 30
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1d028c35ea5d0f00dd8206fbfe0b086c9dbed067
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51724666"
---
# <a name="supported-code-changes-c"></a>Desteklenen Kod Değişiklikleri (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Düzenle ve devam et, metot gövdeleri içinde kod değişiklikleri çoğu türde işler. Metot gövdeleri dışında çoğu değişiklikleri ve metot gövdeleri içindeki bazı değişiklikler, ancak hata ayıklama sırasında uygulanamaz. Desteklenmeyen bu değişiklikleri uygulamak için hata ayıklamayı durdurmak ve kod yeni bir sürümle yeniden başlatmanız gerekir.  
  
 Aşağıdaki değişiklikler, C# kodu için hata ayıklama oturumu sırasında uygulanamaz:  
  
-   Geçerli deyimi veya herhangi bir etkin deyim yapılan değişiklikler.  
  
     Etkin deyimleri için geçerli durumunu almak için çağrılan işlevler çağrı yığını üzerinde herhangi bir deyim ekleyin.  
  
     Geçerli deyimi kaynak penceresinde sarı arka plan olarak işaretlenir. Diğer etkin deyimleri gölgeli bir arka plan işaretlenir ve salt okunurdur. Bu varsayılan renkleri değiştirilebilir **seçenekleri** iletişim kutusu.  
  
-   İmza türü değiştiriliyor.  
  
-   Önce yakalanmayan bir değişken yakalayan bir anonim yöntem ekleniyor.  
  
-   Ekleme, kaldırma veya değiştirme.  
  
-   Ekleme, kaldırma veya değiştirme `using` yönergeleri.  
  
-   Ekleme bir `foreach`, `using`, veya `lock` etkin bir deyim etrafındaki.  
  
## <a name="unsafe-code"></a>Güvenli olmayan kod  
 Güvenli olmayan kod değişiklikleri başka bir kısıtlama ile güvenli kod değişiklikleri onunla aynı sınırlamalara sahiptir: Düzenle ve devam et değişiklikleri içeren bir yöntemi içinde güvenli olmayan kod desteklemiyor `stackalloc` işleci.  
  
## <a name="exceptions"></a>Özel Durumlar  
 Düzenle ve devam et değişiklikleri destekler `catch` ve `finally` ekleme dışında engelleyen bir `catch` veya `finally` blok etkin bir deyim etrafındaki izin verilmiyor.  
  
## <a name="unsupported-scenarios"></a>Desteklenmeyen Senaryolar  
 Düzenle ve devam et hata ayıklama aşağıdaki senaryolarda kullanılabilir değil:  
  
-   Bazı durumlarda LINQ kodda hata ayıklama. Daha fazla bilgi için [LINQ hata ayıklama](../debugger/debugging-linq.md).  
  
    -   Önce yakalanmayan bir değişken yakalama.  
  
    -   Sorgu ifadesi türünün değiştirilmesi (örneğin, a ='ı seçin > Yeni seçme {A = bir};)  
  
    -   Kaldırma bir `where` , etkin bir deyim içerir.  
  
    -   Kaldırma bir `let` , etkin bir deyim içerir.  
  
    -   Kaldırma bir `join` , etkin bir deyim içerir.  
  
    -   Kaldırma bir `orderby` , etkin bir deyim içerir.  
  
-   Karma mod (yerel/yönetilen) hata ayıklama.  
  
-   SQL hata ayıklama.  
  
-   Bir Dr hata ayıklama. Watson dökümü.  
  
-   İşlenmeyen bir özel durumdan sonra kod düzenleme, "**işlenmemiş özel durumlarda çağrı yığınını geriye doğru izleme**" seçeneği belirlenmez.  
  
-   Katıştırılmış çalışma zamanı uygulama hata ayıklama.  
  
-   Sahip bir uygulamada hata ayıklama **ekleme** seçerek uygulamayı çalıştırmak yerine **Başlat** gelen **hata ayıklama** menüsü.  
  
-   En iyi duruma getirilmiş kodda hata ayıklama.  
  
-   Derleme hataları nedeniyle oluşturmak yeni bir sürüm başarısız olduktan sonra kodunuzu eski bir sürümü hata ayıklama.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Düzenle ve devam et (Visual C#)](../debugger/edit-and-continue-visual-csharp.md)   
 [Nasıl Yapılır: Düzenle ve Devam Et'i Kullanma (C#)](../debugger/how-to-use-edit-and-continue-csharp.md)



