---
title: Hata ayıklayıcısı güvenliği | Microsoft Docs
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
- debugging [Visual Studio], security
- debugger, security
- security [Visual Studio], debugging best practices
ms.assetid: d4fc3c43-e844-419c-8dbb-551cc2a9b09e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1032e3db1513f628e540643acf7b1d98f89b5bff
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49865602"
---
# <a name="debugger-security"></a>Hata Ayıklama Güvenliği
Başka bir işlem hata ayıklama olanağı, aksi takdirde, özellikle de uzaktan hata ayıklama yapılırken erişemeyecek çok geniş powers sağlar. Kötü amaçlı bir hata ayıklayıcı hataları ayıklanmakta olan makinede yaygın zarar başını.  
  
 Ancak, birçok geliştiricinin güvenlik tehdidi ters yöne akabilir başlığımız dikkatinizi çekmiş olabilir değil. Hata ayıklanan işlemin hata ayıklama makinesi güvenliğini tehlikeye atabilir, kötü amaçlı kod için mümkündür: bir dizi karşı korumalı olacak güvenlik açıkları vardır.  
  
## <a name="security-best-practices"></a>En İyi Güvenlik Uygulamaları  
 Bir hata ayıklarken kodu ve hata ayıklayıcı arasında örtük güven ilişkisi yoktur. Ayıklamanız istekliyse, aynı zamanda çalıştırmak iradeye sahip olmalıdır. Balonlarının ne ayıkladığınız güvenemez olmalıdır ' dir. Güven olamaz, ardından ayıklama değil veya bir makineden reddetmeniz destekleyebilir ve yalıtılmış bir ortamda ayıklama.  
  
 Olası saldırı yüzeyini azaltmak için hata ayıklama üretim makinelerde devre dışı bırakılmalıdır. Aynı nedenden dolayı hata ayıklama hiç süresiz olarak etkinleştirilmesi gerekir.  
  
### <a name="managed-debugging-security"></a>Yönetilen hata ayıklama güvenlik  
 Aşağıda, tüm yönetilen hata ayıklama uygulanan genel bazı öneriler verilmiştir.  
  
- Güvenilmeyen bir kullanıcının işlemine iliştirme oluştururken dikkatli olun: Bu işlemi gerçekleştirdiğinizde, güvenilir olduğunu varsayın. Güvenilmeyen bir kullanıcının işleme girişiminde bulunduğunuzda bir güvenlik uyarısı iletişim kutusu onayı işleme isteyip istemediğinizi soran görünür. "Kullanıcıların güvenilen", dahil, ve bir dizi standart kullanıcıların yaygın olarak .NET Framework gibi yüklü olan makineler üzerinde tanımlanan **aspnet**, **localsystem**, **networkservice**, ve **localservice**. Daha fazla bilgi için [güvenlik uyarısı: güvenilmeyen bir kullanıcının sahip olduğu işleme ekleme tehlikeli olabilir. Aşağıdaki bilgiler kuşkulu görünüyorsa ya da emin değilseniz, bu işleme eklemeyin](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md).  
  
- Internet ve içine yüklenirken kapalı bir proje indirme işlemi gerçekleştirirken dikkatli olun [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Bu hata ayıklama olmadan bile yapmak için çok risklidir. Bunu yaptığınızda, proje ve içerdiği kod güvenilir olduğunu varsayarak.  
  
  Daha fazla bilgi için [yönetilen kodda hata ayıklama](../debugger/debugging-managed-code.md).  
  
### <a name="remote-debugging-security"></a>Uzaktan hata ayıklama güvenlik  
 Yerel hata ayıklama, uzaktan hata ayıklama daha genellikle güvenlidir. Uzaktan hata ayıklama araştırıldığı toplam yüzey alanını artırır.  
  
 Visual Studio uzaktan hata ayıklama İzleyicisi (msvsmon.exe) uzak hata ayıklama kullanılır ve bu yapılandırma için birçok güvenlik önerileri vardır. Kimlik doğrulama modunu yapılandırmak için tercih edilen yol Windows kimlik doğrulaması, çünkü kimlik doğrulaması yok modu güvenli değil.  
  
 ![Hata iletişim kutusu](../debugger/media/dbg_err_remotepermissionschanged.png "DBG_ERR_RemotePermissionsChanged")  
  
 Windows kimlik doğrulaması modunu kullanırken, kullanıcı, bilgisayar üzerindeki tüm izinler verilir çünkü bir güvenilir olmayan kullanıcı için msvsmon'un bağlanma izni verme tehlikeli olduğundan emin olun...  
  
 Bilinmeyen bir işlem uzak makinede hata ayıklama yok: hata ayıklayıcıyı çalıştıran makinenin etkileyebilir veya msvsmon.exe, Visual Studio uzaktan hata ayıklama İzleyicisi tehlikeye olası açıkları vardır. Kesinlikle bilinmeyen bir işlemde hata ayıklamak gerekir, yerel olarak hata ayıklama deneyin ve yerelleştirilmiş olası tehditlere karşı korumak için bir Güvenlik Duvarı'nı kullanın.  
  
 Daha fazla bilgi için [uzaktan hata ayıklama](../debugger/remote-debugging.md).  
  
### <a name="web-services-debugging-security"></a>Güvenlik hata ayıklamasını web Hizmetleri  
 Yerel olarak hata ayıklama daha güvenlidir, ancak sonra büyük olasılıkla sahip olmadığınız [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] web sunucusunda yüklüyse, yerel hata ayıklama pratik olmayabilir. Genel olarak, Web hizmetlerinde hata ayıklama işlemi, uzaktan, geliştirme sırasında bu nedenle uzaktan hata ayıklama güvenlik önerilerini de hata ayıklama Web Hizmetleri için geçerli dışında gerçekleştirilir. Ek en iyi yöntemlerden bazıları aşağıda verilmiştir. Daha fazla bilgi için [hata ayıklama XML Web Hizmetleri](https://msdn.microsoft.com/library/c900b137-9fbd-4f59-91b5-9c2c6ce06f00).  
  
-   Tehlikede bir Web sunucusunda hata ayıklama etkinleştirmeyin.  
  
-   Web sunucusu güvenli hata ayıklama öncesinde bildiğinizden emin olun. Güvenli olduğundan emin değilseniz, hata ayıklama değil.  
  
-   Internet'te kullanıma sunulan bir Web hizmeti hata ayıklaması yapıyorsanız özellikle dikkatli olun.  
  
### <a name="external-components"></a>Dış bileşenler  
 Özellikle kod yazmadı, programınızı etkileşimde dış bileşenler güven durumunu unutmayın. Ayrıca bileşenlerinin unutmayın, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] veya hata ayıklayıcı kullanabilirsiniz.  
  
### <a name="symbols-and-source-code"></a>Simgeler ve kaynak kodu  
 İki [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] güvenlik göz önünde bulundurulması gereken araçlar şunlardır:  
  
- Kaynak sunucu sürümleriyle kaynak koddan bir kaynak kodu deposu sağlar. Geçerli sürümü, bir programın kaynak koduna sahip durumlarda yararlı olur. [Güvenlik Uyarısı: Hata ayıklayıcı güvenilmeyen komut yürütmeli](../debugger/security-warning-debugger-must-execute-untrusted-command.md).  
  
- Sembol sunucusu, bir sistem çağrısı sırasında bir kilitlenme hatalarını ayıklamak için gerekli sembolleri sağlamak için kullanılır.  
  
  Bkz: [sembol (.pdb) belirtin ve kaynak dosyaları](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata ayıklayıcı ayarları ve hazırlığı](../debugger/debugger-settings-and-preparation.md)   
 [Hata ayıklayıcı temel bilgileri](../debugger/getting-started-with-the-debugger.md)   
 [Güvenlik Uyarısı: Güvenilmeyen bir kullanıcının sahip olduğu işleme ekleme tehlikeli olabilir. Aşağıdaki bilgiler kuşkulu görünüyorsa ya da emin değilseniz, bu işleme eklemeyin.](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)   
 [Güvenlik Uyarısı: Hata Ayıklayıcı Güvenilmeyen Komut Yürütmeli](../debugger/security-warning-debugger-must-execute-untrusted-command.md)