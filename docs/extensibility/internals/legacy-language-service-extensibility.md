---
title: Eski dil hizmeti genişletilebilirliği | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services
- Visual Studio, language services
ms.assetid: 2700cd4d-5f68-43fc-b62f-dc80c3f3aa85
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bb7d8165060fa3b9a6445ad71a977c79414056f3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31129728"
---
# <a name="legacy-language-service-extensibility"></a>Eski dil hizmeti genişletilebilirliği
Bir dil hizmeti IDE kaynak kod düzenleme için dile özgü destek sağlar.  
  
 Eski dil hizmetler bir VSPackage bir parçası olarak uygulanır, ancak dil hizmet özellikleri uygulamak için daha yeni MEF uzantıları kullanmak için bir yoludur. Bir dil hizmeti uygulamak için yeni yolu hakkında daha fazla bilgi için bkz: [Düzenleyicisi ve dil hizmeti uzantılarını](../../extensibility/editor-and-language-service-extensions.md).  
  
 Bu bölümde, yapı ve eski dil hizmeti uygulaması açıklanmaktadır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Eski Dil Hizmetini Geçirme](../../extensibility/internals/migrating-a-legacy-language-service.md)  
 Visual Studio 2008 bir dil Hizmeti'nden en son sürüme güncelleştirmek açıklanmaktadır.  
  
 [Eski Dil Hizmeti Temel Bileşenleri](../../extensibility/internals/legacy-language-service-essentials.md)  
 Bir programlama dili Visual Studio'ya tümleştirmek için dil Hizmetleri geliştirme hakkında önemli bilgileri sağlar.  
  
 [Eski Dil Hizmeti Geliştirme](../../extensibility/internals/developing-a-legacy-language-service.md)  
 Bir dil hizmeti oluşturmanıza yardımcı olabilir konulara bağlantılar sağlar.  
  
 [Eski Dil Hizmetinde Söz Dizimi Renklendirmesi](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)  
 Bir dil hizmetinde sözdizimi vurgulama destekleme hakkında bilgi sağlar.  
  
 [Eski dil hizmeti uygulama](../../extensibility/internals/implementing-a-legacy-language-service1.md)  
 Yönetilen paket framework (MPF) tam özellikli dil hizmeti yönetilen koda uygulanması için nasıl kullanılacağı hakkında bilgi sağlar.  
  
 [Sembol Tarama Araçlarını Destekleme](../../extensibility/internals/supporting-symbol-browsing-tools.md)  
 Kitaplıkları ve IDE içinde simgelerin ağaç görünümleri Gözat sağlayan araçlar açıklanmaktadır.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Düzenleyici ve Dil Hizmeti Uzantıları](../../extensibility/editor-and-language-service-extensions.md)  
 Visual Studio düzenleyicileri genel bir bakış sağlar.  
  
 [Hata Ayıklama için Dil Hizmeti Desteği](../../extensibility/internals/language-service-support-for-debugging.md)  
 Visual Studio hata ayıklama oluşturmak ve programların hatalarını ayıklamak için kullanılan hata ayıklayıcı bileşenleri özelleştirmek için gerekli olan bilgileri içeren SDK için ilgili bilgileri ve bağlantı sağlar.