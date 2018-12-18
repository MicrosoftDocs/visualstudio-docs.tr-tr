---
title: Yönetilen kodda hata ayıklama | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging managed code
- debugging ASP.NET Web applications, managed code
- managed code, debugging
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 92485f93bb4c2d1782f907acdb1e5252f611cdbe
ms.sourcegitcommit: bc43970c000f07c9cc2051f1264a9742943a9755
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2018
ms.locfileid: "39179485"
---
# <a name="debugging-managed-code"></a>Yönetilen Kodda Hata Ayıklama

Bu bölüm yaygın hata ayıklama sorunları ve yönetilen uygulamalar için teknikleri kapsar veya uygulamalarda yazıldığına dillerde hedefleyen Visual Basic, C# ve C++ gibi ortak dil çalışma zamanı. Burada açıklanan teknikleri, üst düzey tekniklerle aynıdır. Daha fazla bilgi için [hata ayıklayıcıyı kullanma](../debugger/getting-started-with-the-debugger.md).

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
Yönetilen kodda hata ayıklama çalışırsanız oluşan bir hata iletisi açıklayan bir [!INCLUDE[win7](../debugger/includes/win7_md.md)], [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)], [!INCLUDE[winxp](../code-quality/includes/winxp_md.md)], [!INCLUDE[Win2kFamily](../code-quality/includes/win2kfamily_md.md)], veya hata ayıklama modunda başlatıldı Windows NT sistem.

[JIT İyileştirmesi ve Hata Ayıklaması](../debugger/jit-optimization-and-debugging.md)  
Hata ayıklamayı JIT iyileştirmesini etkilerini açıklar.

[LINQ ve DLINQ hata ayıklama](../debugger/debugging-linq.md)  
LINQ sorguları hata ayıklama teknikleri açıklar.

[İzlenecek Yol: Paralel Uygulamada Hata Ayıklama](../debugger/walkthrough-debugging-a-parallel-application.md)  
Nasıl kullanılacağını açıklar **Paralel Görevler** ve **Paralel Yığınlar** paralel uygulamada hata ayıklamak için windows aracı.

## <a name="related-sections"></a>İlgili Bölümler

[IntelliTrace](../debugger/intellitrace.md) IntelliTrace ile uygulamanızın yürütme geçmişini kaydederek hataları daha hızlı ve daha kolay bulun. Geri adım ve kaydedilen olaylarını ve zamanında önemli anlarda uygulamanızın durumunu incelemek için çağrılar aracılığıyla iletebilir. Kodunuzdaki hataları ayıklamanıza sayıda kesme noktası ayarlama veya sık olarak uygulamanızı yeniden başlatmadan olmadan. Visual Studio Enterprise gereklidir.

[İzleme ve İşaretleme Uygulamaları](/dotnet/framework/debug-trace-profile/tracing-and-instrumenting-applications)  
İzleme, onu çalıştıran ve izleme, ancak uygulamanızın yürütmesini izlemek bir yol açıklar izleme deyimleri kodunuzda stratejik konumlara yerleştirerek içerir. İzleme anahtarları, izleme dinleyicileri bir uygulamadaki kodu izleme, uygulama koduna izleme deyimleri ekleme ve ile koşullu derleme, izleme, bu konuda ayrıca izleme için bir giriş için bağlantılar sağlar ve <xref:System.Diagnostics.Debug> ve <xref:System.Diagnostics.Trace> .

[/ ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute)  
Ekleyen bir bağlayıcı seçeneği açıklar <xref:System.Diagnostics.DebuggableAttribute> C++ ile yazılmış kodu. Bu öznitelik, hata ayıklama kullanmak için gerekli olan özellikleri gibi C++ ile ekleyin.

[Hata ayıklama Windows hizmet uygulamaları](/dotnet/framework/windows-services/how-to-debug-windows-service-applications)  
Windows hizmet uygulamalarında hata ayıklama, kurma da dahil olmak üzere, işlemine iliştirme, hizmetin kodda hata ayıklama ile ilgili konuları sağlar `OnStart` yöntemi ve kodda kesme noktaları ayarlama ve Hizmetleri denetimi kullanarak ana yöntemi Başlatma, durdurma, duraklatma ve devam hizmetiniz için manager'ı tıklatın.

[Hata ayıklama ve profil oluşturma](/dotnet/framework/debug-trace-profile/index)  
Hata ayıklama .NET Framework uygulamaları ve yapılandırma gereksinimleri açıklanır.

[Betik ve Web uygulamalarında hata ayıklama](../debugger/debugging-web-applications-and-script.md)  
Genel hata ayıklama sorunları ve komut dosyası ve Web uygulamalarında hata ayıklama sırasında karşılaşabileceğiniz teknikleri açıklar.

[Hata Ayıklayıcı'Visual Studio 2015'teki yenilikler](../debugger/what-s-new-for-the-debugger-in-visual-studio.md)  
Bu sürümde eklenen yeni hata ayıklama özellikleri açıklaması [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

[Giriş sayfasının hatalarını ayıklama](../debugger/debugger-feature-tour.md)  
Hata ayıklama belgesinin en geniş bölümlerine bağlantılar sağlar. Bilgileri içeren hata ayıklayıcı, ayarlar ve hazırlık, kesme noktaları, özel durumların işlenmesi yenilikler Düzenle ve devam et, yönetilen kodda hata ayıklama, Visual C++ projelerinde hata ayıklama, COM ve ActiveX hata ayıklaması, DLL'lerinde hata ayıklama, SQL ve kullanıcı hata ayıklama arabirimi başvuruları.

## <a name="see-also"></a>Ayrıca bkz.

[İzlenecek yol: Özel Windows hata ayıklama denetimleri tasarım zamanında Forms](/dotnet/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time)
[hata ayıklayıcı, güvenlik](../debugger/debugger-security.md)
[Visual Studio'da hata ayıklama](../debugger/index.md) 
 [ Hata ayıklayıcısı özellik turu](../debugger/debugger-feature-tour.md)