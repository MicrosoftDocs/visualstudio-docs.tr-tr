---
title: Visual Studio hata ayıklayıcı genişletilebilirliği | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Visual Studio], Debugging SDK
- Debugging SDK
ms.assetid: c088b6a2-c3ad-446b-830d-9c6f41b2934b
caps.latest.revision: 33
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8b5e9e7a3db38b5138f6392ff89f3a3bb4a13303
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51743488"
---
# <a name="visual-studio-debugger-extensibility"></a>Visual Studio Hata Ayıklayıcı Genişletilebilirliği
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Visual Studio, programınızdaki hataları aşağı izlemek için güçlü ve kullanımı kolay bir araç sağlayan bir tam etkileşimli kaynak kodu hata ayıklayıcı, içerir. Hata ayıklayıcı tam destek Visual Basic, C#, C/C++ ve JavaScript sahiptir. Bununla birlikte, [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)], yani kullanılabilir [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=214453), hata ayıklayıcı aynı zengin özelliklere sahip başka bir programlama dili desteklenebilir.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Hata ayıklayıcısı, hataları ayıklanan diline özgü buna karşılık olarak hata ayıklama bileşenlerini genel ön uç (diğer bir deyişle, kullanıcı arabirimi) etmektir. İçin gerekli olan tüm yeni diller için destek [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] hata ayıklayıcı, hata ayıklama altyapısı (DE) gibi gerekli arka uç bileşenlerine oluşturmaktır. Olduğu yer [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] halinde sunulur.  
  
 [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] Tüm eksiksiz bir başvuru içeriyor [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] yeni DE oluşturmak için gereken öğeleri. Ayrıca, örnekler ve başlamanıza yardımcı olacak öğreticiler vardır.  
  
 Hata ayıklama desteği ile dil proje sistemi bir uçtan uca örnek için bkz: [IronPython örnek](http://msdn.microsoft.com/en-us/4c41695c-12c1-4670-b43b-d8d84c9e4089).  
  
 Aşağıdaki bölümlerde kullanarak hata ayıklayıcıyı genişletmek nasıl [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)].  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Başlarken](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)  
 Neler açıklanır [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] teklifler ve SDK'yı yüklemeyi nasıl hata ayıklama.  
  
 [Özel Hata Ayıklama Altyapısı Oluşturma](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Programınızı DE ayırmak için bir DE hazırlama özel DE işlemin, belgeler.  
  
 [CLR İfade Değerlendirici Yazma](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
 İfade değerlendiricisi yazma olup olmadığını açıklar.  
  
 [Hata Ayıklama Altyapısı Uygulama Stratejisi Seçme](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md)  
 Sizin DE uygulamak nasıl ele alınmaktadır.  
  
 [Başvuru](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md)  
 Belgeler [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] hata ayıklama API'si.  
  
 [Örnekler](../../extensibility/debugger/visual-studio-debugging-samples.md)  
 Bir ortak dil çalışma zamanı ifade değerlendiricisi örneği ve bir hata ayıklama altyapısı örneği bağlantılar içerir.

