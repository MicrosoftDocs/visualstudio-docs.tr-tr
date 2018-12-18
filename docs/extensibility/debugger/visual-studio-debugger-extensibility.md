---
title: Visual Studio hata ayıklayıcı genişletilebilirliği | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Debugging SDK
- Debugging SDK
ms.assetid: c088b6a2-c3ad-446b-830d-9c6f41b2934b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b0be4a96854315bcf8b83db86692758e198980cd
ms.sourcegitcommit: 3dd15e019cba7d35dbabc1aa3bf55842a59f5278
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46370932"
---
# <a name="visual-studio-debugger-extensibility"></a>Visual Studio hata ayıklayıcı genişletilebilirliği
Visual Studio, programınızdaki hataları aşağı izlemek için güçlü ve kullanımı kolay bir araç sağlayan bir tam etkileşimli kaynak kodu hata ayıklayıcı, içerir. Hata ayıklayıcı tam destek Visual Basic, C#, C/C++ ve JavaScript sahiptir. Bununla birlikte, [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], yani kullanılabilir [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=214453), hata ayıklayıcı aynı zengin özelliklere sahip başka bir programlama dili desteklenebilir.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Hata ayıklayıcısı, hataları ayıklanan diline özgü buna karşılık olarak hata ayıklama bileşenlerini genel ön uç (diğer bir deyişle, kullanıcı arabirimi) etmektir. İçin gerekli olan tüm yeni diller için destek [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] hata ayıklayıcı, hata ayıklama altyapısı (DE) gibi gerekli arka uç bileşenlerine oluşturmaktır. Bu noktaya yerdir [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] halinde sunulur.  
  
 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] Tüm eksiksiz bir başvuru içeriyor [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] yeni DE oluşturmak için gereken öğeleri. Ayrıca, örnekler ve başlamanıza yardımcı olacak öğreticiler vardır.  
  
 Hata ayıklama desteği ile bir dil proje sisteminin eksiksiz bir örnek için bkz. [IronPython örnek](https://www.microsoft.com/download/details.aspx?id=55984).  
  
 Aşağıdaki bölümlerde kullanarak hata ayıklayıcıyı genişletmek nasıl [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)].  
  
## <a name="in-this-section"></a>Bu bölümde  
 [Kullanmaya başlama](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)  
 Neler açıklanır [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] teklifler ve SDK'yı yüklemeyi nasıl hata ayıklama.  
  
 [Bir özel hata ayıklama altyapısı oluşturma](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Programınızı DE ayırmak için bir DE hazırlama özel DE işlemin, belgeler.  
  
 [Bir CLR ifade değerlendiricisi yazma](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
 İfade değerlendiricisi yazma olup olmadığını açıklar.  
  
 [Hata ayıklama altyapısı uygulama stratejisi seçme](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md)  
 Sizin DE uygulamak nasıl ele alınmaktadır.  
  
 [Başvuru](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md)  
 Belgeler [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] hata ayıklama API'si.  
  
 [Örnekler](../../extensibility/debugger/visual-studio-debugging-samples.md)  
 Bir ortak dil çalışma zamanı ifade değerlendiricisi örneği ve bir hata ayıklama altyapısı örneği bağlantılar içerir.
