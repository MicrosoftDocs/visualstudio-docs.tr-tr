---
title: Düzenle ve devam et hata iletisi iletişim kutusu | Microsoft Docs
ms.custom: ''
ms.date: 10/15/2018
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.ENC.SupportedButNotAvaiable
- vs.debug.ENC.CannotEditWhileException
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue Error Message dialog box
ms.assetid: f98c91c0-447a-4533-85b6-87170a0dc4c3
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ba573a6b6bffdfeebf37c5f46f1f774d699a1131
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52388718"
---
# <a name="edit-and-continue-error-message"></a>Düzenle ve devam et hata iletisi 

**Düzenle ve devam et** Düzenle ve devam et destekleyen bir kod dili ayıklanırken hata ileti kutusu görünür, ancak Düzenle ve devam et yaptığınız kod değişiklikleri için kullanılabilir değildir. Hata iletisi daha ayrıntılı bir açıklama sağlar. İletişim kutusuna yanıt vermek için seçin **Tamam** iletişim kutusunu kapatmak ve düzenleme denemesi iptal etmek için.  

Bu hata iletisi için olası nedenler şunlardır:  

-   SQL Server kod düzenlemek çalışıyor.
-   En iyi duruma getirilmiş kod düzenlemek çalışıyor. Yayın derleme için hata ayıklama derlemesi geçmeniz gerekebilir.
-   Çalışırken, kod düzenlemeye çalışmak yerine hata ayıklayıcıda duraklatıldığı sırada. Deneyin [bir kesme noktası ayarlamak](../debugger/using-breakpoints.md)ve duraklatıldığı sırada kod düzenleme.
-   Yalnızca yönetilmeyen hata ayıklama etkinleştirildiğinde, yönetilen kod düzenlemek çalışıyor. Düzenle ve devam et ile çalışmıyor [karışık mod hata ayıklama](../debugger/how-to-debug-in-mixed-mode.md).
-   Düzenle ve devam et tarafından bir kod, değişikliği yapmadan programlama diliniz desteklenmez. Daha fazla bilgi için bkz: makaleler [C# ' de desteklenen kod değişiklikleri](supported-code-changes-csharp.md), [desteklenmeyen düzenlemeler, Visual Basic Düzenle ve devam et](unsupported-edits-in-visual-basic-edit-and-continue.md), ve [desteklenen kod değişiklikleri C++](supported-code-changes-cpp.md).
-   Bağlı için hata ayıklamayı başlatma yerine uygulama kodları düzenlemeye çalıştığınız **hata ayıklama** menüsü.  
-   Bir Dr hata ayıklarken kod düzenlemek çalışıyor. Watson dökümü.  
-   İşlenmeyen bir özel durum oluştuktan sonra kod düzenlemeye çalıştığınız ve seçeneği **işlenmemiş özel durumlarda çağrı yığınını geriye doğru izleme** seçilmez.  
-   Kod katıştırılmış çalışma zamanı uygulamasında hata ayıklaması sırasında düzenlemek çalışıyor.
-   .NET Framework sürüm 4.5.1'den önceki bir 64 bit uygulama hedefle kullanarak yönetilen kod düzenlemek çalışıyor. Düzenle ve devam et için .NET Framework 4.5.1'den önceki kullanmak için hedef ayarlanmış **x86** içinde  **\<ProjectName >** > **özellikleri**  >  **Derleme** sekmesinde **Gelişmiş derleyici** ayarı.  
-   Hata ayıklama sırasında değiştirildi ve yeniden yüklendi bütünleştirilmiş kodu düzenleme çalışılıyor.  
-   Yüklenmemiş bir derleme kodu düzenleme çalışılıyor.  
-   Derleme hataları en son sürüme sahip olduğu bir uygulama eski bir sürümü hata ayıklamayı başlatma.
  
Daha fazla bilgi için bkz.:
- [C++ Düzenle ve devam et blog gönderisini](https://blogs.msdn.microsoft.com/vcblog/2016/07/01/c-edit-and-continue-in-visual-studio-2015-update-3/)  
- [Desteklenen kod değişiklikleri (C++)](../debugger/supported-code-changes-cpp.md)
- [Düzenle ve Devam Et](../debugger/edit-and-continue.md)