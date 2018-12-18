---
title: 'Nasıl yapılır: projeleri hedef platformlar için yapılandırma | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- project settings [Visual Studio], targeting platforms
- platforms, targeting specific CPUs
- project properties [Visual Studio], targeting platforms
- projects [Visual Studio], targeting platforms
- 64-bit [Visual Studio]
- 64-bit programming [Visual Studio]
- CPUs, targeting specific
- 64-bit applications [Visual Studio]
ms.assetid: 845302fc-273d-4f81-820a-7296ce91bd76
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4e2b39aa13316b1b9ca47c5587ffabf6f6a14e68
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49843060"
---
# <a name="how-to-configure-projects-to-target-platforms"></a>Nasıl Yapılır: Projeleri Hedef Platformlar İçin Yapılandırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] uygulamalarınızı 64 bit platformlar da dahil olmak üzere, farklı platformları hedeflemek için ayarlamanıza imkan sağlar. 64-bit platformu hakkında daha fazla bilgi için destek [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], bkz: [64-bit uygulamalar](http://msdn.microsoft.com/library/fd4026bc-2c3d-4b27-86dc-ec5e96018181).  
  
## <a name="targeting-platforms-with-the-configuration-manager"></a>Configuration Manager ile platformlarını hedefleyen  
 **Configuration Manager** projenizle hedef hızla yeni bir platform eklemek bir yol sağlar. Bulunan platformlardan birini seçerseniz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], projeniz için özellikleri seçilen platform için projenizi yaratmanız için değiştirilmiştir.  
  
#### <a name="to-configure-a-project-to-target-a-64-bit-platform"></a>Bir 64 bit platformları hedefleyen bir proje yapılandırma  
  
1. Menü çubuğunda, **derleme**, **Configuration Manager**.  
  
2. İçinde **etkin çözüm platformu** listesinde, hedef çözümü için 64 bit platform seçin ve ardından **Kapat** düğmesi.  
  
   1.  İstediğiniz platform görünmüyorsa **etkin çözüm platformu** listesinde **yeni**.  
  
        **Yeni çözüm platformu** iletişim kutusu görüntülenir.  
  
   2.  İçinde **yazın veya seçin yeni platformu** listesinde **x64**.  
  
       > [!NOTE]
       >  Yapılandırmanızı yeni bir ad verin, ayarlarını değiştirmeniz gerekebilir **Proje Tasarımcısı** doğru platformunu hedeflemek için.  
  
   3.  Geçerli bir platform yapılandırmasını ayarlar kopyalamak istiyorsanız, bunu seçin ve ardından **Tamam** düğmesi.  
  
   64-bit platformu hedefleyen tüm projeler için özellikler güncelleştirilir ve projenin sonraki derleme için 64-bit platformlarda iyileştirilir.  
  
## <a name="targeting-platforms-in-the-project-designer"></a>Proje Tasarımcısı'nda platformlarını hedefleyen  
 Proje Tasarımcısı, ayrıca projenizle farklı platformları hedeflemek için bir yol sağlar. Listede bulunan platformlardan birini seçilirken **yeni çözüm platformu** iletişim kutusunda, çözümünüz için çalışmıyor, özel yapılandırma adı oluşturmak ve ayarlarını değiştirmeyi **Proje Tasarımcısı**  doğru platformunu hedeflemek için.  
  
 Bu görevi gerçekleştirmek, kullandığınız programlama diline göre değişir. Daha fazla bilgi için aşağıdaki bağlantılara bakın:  
  
-   İçin [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] projeleri için bkz: [/Platform (Visual Basic)](http://msdn.microsoft.com/library/f9bc61e6-e854-4ae1-87b9-d6244de23fd1).  
  
-   İçin [!INCLUDE[csprcs](../includes/csprcs-md.md)] projeleri için bkz: [derleme sayfası, Proje Tasarımcısı (C#)](../ide/reference/build-page-project-designer-csharp.md).  
  
-   İçin [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] projeleri için bkz: [/CLR (ortak dil çalışma zamanı derlemesi)](http://msdn.microsoft.com/library/fec5a8c0-40ec-484c-a213-8dec918c1d6c).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Derleme platformlarını anlama](../ide/understanding-build-platforms.md)   
 [/ Platform (C# Derleyici Seçenekleri)](http://msdn.microsoft.com/library/c290ff5e-47f4-4a85-9bb3-9c2525b0be04)   
 [64-bit uygulamalar](http://msdn.microsoft.com/library/fd4026bc-2c3d-4b27-86dc-ec5e96018181)   
 [Visual Studio IDE 64 Bit Desteği](../ide/visual-studio-ide-64-bit-support.md)



