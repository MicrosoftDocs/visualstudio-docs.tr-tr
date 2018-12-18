---
title: Yönetilen kodda hata ayıklama | Microsoft Docs
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
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging managed code
- debugging ASP.NET Web applications, managed code
- managed code, debugging
ms.assetid: fa3aff01-c271-4aa7-b5b1-def560471c84
caps.latest.revision: 37
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 801a4654b2297e3c19929063716339c7a4fcd50b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51774425"
---
# <a name="debugging-managed-code"></a>Yönetilen Kodda Hata Ayıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu bölüm yaygın hata ayıklama sorunları ve yönetilen uygulamalar için teknikleri kapsar veya uygulamalarda yazıldığına dillerde hedefleyen Visual Basic, C# ve C++ gibi ortak dil çalışma zamanı. Burada açıklanan teknikleri, üst düzey tekniklerle aynıdır. Daha fazla bilgi için [hata ayıklayıcıyı kullanma](../debugger/debugger-basics.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Çıkış Penceresindeki Tanılama İletileri](../debugger/diagnostic-messages-in-the-output-window.md)  
 Açıklar <xref:System.Diagnostics.Debug> ve <xref:System.Diagnostics.Trace> sınıfları, çalışma zamanı iletileri ile yazabileceğiniz **çıkış** penceresi. Bu sınıflar, belirtilen bir koşulu başarısız olursa da yürütmeyi keser yürütme ve bilgi çıkış bozmadan bilgi çıkışı etkinleştir çıkış yöntemleri kapsar.  
  
 [Yönetilen Koddaki Onaylamalar](../debugger/assertions-in-managed-code.md)  
 Bağımsız değişken olarak belirttiğiniz koşullara test yönetilen koddaki onaylar açıklar `Assert` yöntemleri. Ayrıca, bu konu örnek kod, hakkında bilgi sağlar <xref:System.Diagnostics.Debug> ve <xref:System.Diagnostics.Trace> sınıfı yöntemleri, kodun, yan etkileri, hata ayıklama ve yayın sürümleri hususlarına assert bağımsız değişkenler, özelleştirme assert davranışı ve yapılandırma dosyaları.  
  
 [Visual Basic'de Durdur Deyimleri](../debugger/stop-statements-in-visual-basic.md)  
 Açıklar `Stop` bir kesme noktası ayarlamak için bir alternatif sağlayan bir ifade. Örnek kod ayrıca sağlanan, arasında karşılaştırma birlikte `Stop` deyimi ve `End` arasında iyi gibi olarak bir deyim `Stop` ve `Assert` deyimi.  
  
 [İzlenecek yol: Windows Formunda hata ayıklama](../debugger/walkthrough-debugging-a-windows-form.md)  
 Bir Windows formu oluşturma ve bu formunda hata ayıklama için adım adım yönergeler sağlar. Windows Form, yönetilen bir Windows uygulamasının standart bir bileşen en yaygın yönetilen uygulamalardan biridir. Bu izlenecek yol, Visual C# ve Visual Basic kullanan, ancak C++ ile bir Windows formu oluşturma tekniklerini genellikle benzerdir.  
  
 [OnStart metodunda hata ayıklama](../debugger/how-to-debug-the-onstart-method.md)  
 Hata ayıklama için izin vermek için kod örnekleri sağlar `OnStart` yöntemi bir Windows hizmetidir. Hata ayıklamak için `OnStart` yöntemi bir Windows hizmetinin Hizmet benzetimini yapmak için kodu birkaç satır kod eklemeniz gerekir.  
  
 [Karışık mod hata ayıklama](../debugger/debugging-mixed-mode-applications.md)  
 Karışık mod uygulamalarında hata ayıklama açıklanır. Bu, yerel kod yönetilen kodu ile bir araya getiren herhangi bir uygulama anlamına gelir.  
  
 [Hata: Sistemde çekirdek hata ayıklayıcı etkinleştirildiğinden hata ayıklama mümkün değil](../debugger/error-debugging-isn-t-possible-because-a-kernel-debugger-is-enabled-on-the-system.md)  
 Yönetilen kodda hata ayıklama çalışırsanız oluşan bir hata iletisi açıklayan bir [!INCLUDE[win7](../includes/win7-md.md)], [!INCLUDE[wiprlhext](../includes/wiprlhext-md.md)], [!INCLUDE[winxp](../includes/winxp-md.md)], [!INCLUDE[Win2kFamily](../includes/win2kfamily-md.md)], veya hata ayıklama modunda başlatıldı Windows NT sistem.  
  
 [JIT İyileştirmesi ve Hata Ayıklaması](../debugger/jit-optimization-and-debugging.md)  
 Hata ayıklamayı JIT iyileştirmesini etkilerini açıklar.  
  
 [LINQ ve DLINQ hata ayıklama](../debugger/debugging-linq.md)  
 LINQ sorguları hata ayıklama teknikleri açıklar.  
  
 [İzlenecek Yol: Paralel Uygulamada Hata Ayıklama](../debugger/walkthrough-debugging-a-parallel-application.md)  
 Nasıl kullanılacağını açıklar **Paralel Görevler** ve **Paralel Yığınlar** paralel uygulamada hata ayıklamak için windows aracı.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [IntelliTrace](../debugger/intellitrace.md)  
 IntelliTrace ile uygulamanızın yürütme geçmişini kaydederek hataları daha hızlı ve daha kolay bulun. Geri adım ve kaydedilen olaylarını ve zamanında önemli anlarda uygulamanızın durumunu incelemek için çağrılar aracılığıyla iletebilir. Kodunuzdaki hataları ayıklamanıza sayıda kesme noktası ayarlama veya sık olarak uygulamanızı yeniden başlatmadan olmadan. Visual Studio Ultimate gerekir.  
  
 [İzleme ve İşaretleme Uygulamaları](http://msdn.microsoft.com/library/773b6fc4-9013-4322-b728-5dec7a72e743)  
 İzleme, onu çalıştıran ve izleme, ancak uygulamanızın yürütmesini izlemek bir yol açıklar izleme deyimleri kodunuzda stratejik konumlara yerleştirerek içerir. İzleme anahtarları, izleme dinleyicileri bir uygulamadaki kodu izleme, uygulama koduna izleme deyimleri ekleme ve ile koşullu derleme, izleme, bu konuda ayrıca izleme için bir giriş için bağlantılar sağlar ve <xref:System.Diagnostics.Debug> ve <xref:System.Diagnostics.Trace> .  
  
 [/ ASSEMBLYDEBUG](http://msdn.microsoft.com/library/94443af3-470c-41d7-83a0-7434563d7982)  
 Ekleyen bir bağlayıcı seçeneği açıklar <xref:System.Diagnostics.DebuggableAttribute> C++ ile yazılmış kodu. Bu öznitelik, hata ayıklama kullanmak için gerekli olan özellikleri gibi C++ ile ekleyin.  
  
 [Hata ayıklama Windows hizmet uygulamaları](http://msdn.microsoft.com/library/63ab0800-0f05-4f1e-88e6-94c73fd920a2)  
 Windows hizmet uygulamalarında hata ayıklama, kurma da dahil olmak üzere, işlemine iliştirme, hizmetin kodda hata ayıklama ile ilgili konuları sağlar `OnStart` yöntemi ve kodda kesme noktaları ayarlama ve Hizmetleri denetimi kullanarak ana yöntemi Başlatma, durdurma, duraklatma ve devam hizmetiniz için manager'ı tıklatın.  
  
 [Hata ayıklama ve profil oluşturma](http://msdn.microsoft.com/library/4a04863e-2475-46f4-bc3f-3c11510c2a4b)  
 Hata ayıklama .NET Framework uygulamaları ve yapılandırma gereksinimleri açıklanır.  
  
 [Betik ve Web uygulamalarında hata ayıklama](../debugger/debugging-web-applications-and-script.md)  
 Genel hata ayıklama sorunları ve komut dosyası ve Web uygulamalarında hata ayıklama sırasında karşılaşabileceğiniz teknikleri açıklar.  
  
 [Visual Studio 2015'te Hata Ayıklayıcısı Yenilikleri](../debugger/what’s-new-for-the-debugger-in-visual-studio-2015.md)  
 Bu sürümde eklenen yeni hata ayıklama özellikleri açıklaması [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
 [Giriş sayfasının hatalarını ayıklama](../debugger/debugging-in-visual-studio.md)  
 Hata ayıklama belgesinin en geniş bölümlerine bağlantılar sağlar. Bilgileri içeren hata ayıklayıcı, ayarlar ve hazırlık, kesme noktaları, özel durumların işlenmesi yenilikler Düzenle ve devam et, yönetilen kodda hata ayıklama, Visual C++ projelerinde hata ayıklama, COM ve ActiveX hata ayıklaması, DLL'lerinde hata ayıklama, SQL ve kullanıcı hata ayıklama arabirimi başvuruları.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek yol: Özel Windows hata ayıklama tasarım zamanında Forms denetimleri](http://msdn.microsoft.com/library/1fd83ccd-3798-42fc-85a3-6cba99467387)   
 [Hata ayıklayıcısı güvenliği](../debugger/debugger-security.md)   
 [Visual Studio’da hata ayıklama](../debugger/debugging-in-visual-studio.md)



