---
title: Proje bir Visual Basic hata ayıklama yapılandırması ayarları | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vbProjectPropertiesDebug
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- project settings [Visual Studio], debug configurations
- debug builds, project settings
- debugging [Visual Basic], debugger settings
- projects [Visual Studio], debug configurations
- project configurations, debug
- debug configurations, Visual Basic
ms.assetid: 72a8483a-af0b-4403-8b0d-ee9ad71ee435
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f3b221af6267966a9621d7926c3aeb5aa684cdad
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51735976"
---
# <a name="project-settings-for-a-visual-basic-debug-configuration"></a>Visual Basic Hata Ayıklama Yapılandırması Proje Ayarları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Proje ayarlarını değiştirebilirsiniz bir [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] hata ayıklama yapılandırmasında **özellik sayfaları** anlatıldığı gibi penceresinde [hata ayıklama ve yayın yapılandırmaları](../debugger/how-to-set-debug-and-release-configurations.md). Aşağıdaki tablolarda, hata ayıklayıcı ile ilgili ayarların nerede bulunacağı gösterilmektedir **özellik sayfaları** penceresi.  
  
> [!WARNING]
>  Bu konuda Store uygulamaları için geçerli değildir. Bkz: [(VB, C#, C++ ve XAML) bir hata ayıklama oturumu başlatın](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)  
  
### <a name="debug-tab"></a>Hata ayıklama sekmesi  
  
|Ayar|Açıklama|  
|-------------|-----------------|  
|**Yapılandırma**|Uygulama derlemek için modu ayarlar. Arasından seçim **etkin (hata ayıklama)**, **hata ayıklama**, **yayın**, **yapılandırmalarında**.|  
|**Başlatma eylemi**|Bu grubu denetimleri, hata ayıklama menüsünden Başlangıç meydana gelir eylemi belirtir.<br /><br /> -   **Proje başlangıç** varsayılandır ve hata ayıklama için başlangıç projesi başlatır. Daha fazla bilgi için [NIB nasıl yapılır: Başlangıç projelerini Ayarla](http://msdn.microsoft.com/en-us/31465836-0911-48db-a5d9-e456b635e970).<br />-   **Harici program Başlat** başlatmak ve olmayan bir programa ekledikten sağlayan parçası olan bir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] proje. Daha fazla bilgi için [çalışan işlemlere ekleme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).<br />-   **URL'de tarayıcı başlatmak** bir Web uygulaması ayıklamanızı sağlar.|  
|**Komut satırı bağımsız değişkenleri**|Ayıklanacak programın komut satırı bağımsız değişkenlerini belirtir. Komut başlangıç dış program içinde belirtilen program adı addır. Başlatma eylemi için başlangıç URL'si olarak ayarlanırsa, komut satırı bağımsız değişkenleri göz ardı edilir.|  
|**Çalışma dizini**|Ayıklanan programın çalışma dizini belirtir. İçinde [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], çalışma dizini uygulamayı başlatan dizindir. Varsayılan çalışma dizini, \bin\Debug veya geçerli yapılandırmasına bağlı olarak, \bin\Release bağlıdır.|  
|**Uzak makine kullanma**|Uzaktan hata ayıklama, onay kutusu seçili olduğunda etkindir. Metin kutusunda, hata ayıklama amacıyla nerede uygulamanın çalışacağı uzak bir makine adını yazın veya bir [Msvsmon sunucu adı](http://msdn.microsoft.com/library/55b60ce7-834b-4e83-a10e-fe4248260a4c). Uzak makinede EXE konumunu derleme sekmesi çıkış yolu özelliği tarafından belirtilir. Konum, uzak makinede paylaşılabilir bir dizin olmalıdır.|  
|**Yönetilmeyen kodda hata ayıklama**|Yerel (yönetilmeyen) Win32 koddaki çağrıları yönetilen uygulamanızın hatalarını ayıklamanızı sağlar. Bu hata ayıklayıcı türü için karma seçerek aynı etkiye sahip bir [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] proje.|  
|**SQL Server hata ayıklama**|SQL Server veritabanı nesnelerini hata ayıklamasını sağlar.|  
  
### <a name="compile-tab-press-advanced-compile-options-button"></a>Sekme derle: Gelişmiş derleme seçenekleri düğmesine basın  
  
|Ayar|Açıklama|  
|-------------|-----------------|  
|**Eniyileştirmeleri etkinleştir**|Bu seçenek işaretinin kaldırılması gerekir. En iyi duruma getirme neden görünen kaynak kodundan farklı olacak şekilde gerçekte çalıştırılan kod [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]ve bu nedenle hata ayıklaması zor yapar. Kodun en iyilenmesi ise sembolleri olmayan yüklenemeyen varsayılan olarak yalnızca kendi kodum'hata ayıklama sırasında.|  
|**Hata ayıklama bilgileri üret**|Varsayılan olarak, hem hata ayıklama ve yayın tarafından tanımlanan sürümleri, bu (/ debug derleyici seçeneği eşdeğer) ayarı oluşturur hata ayıklama bilgileri oluşturma zamanında. Hata ayıklayıcı, hata ayıklaması yapıyorsanız kullanışlı bir formda değişken adları ve diğer bilgileri göstermek için bu bilgileri kullanır. Programınızın bu bilgiler olmadan derleme yaparsanız, hata ayıklayıcı işlevselliği sınırlı olacaktır. Daha fazla bilgi için [/debug](http://msdn.microsoft.com/library/c2b0bea5-1d5e-499f-9bd5-4f6c6b715ea2).|  
|**DEBUG sabitini tanımlayın**|Bu sembol tanımlama sağlayan çıkış işlevlerin koşullu derleme [hata ayıklama sınıfı](https://msdn.microsoft.com/library/system.diagnostics.debug.aspx). Tanımlanan bu simge ile hata ayıklama sınıfı yöntemleri çıkışı Oluştur [çıkış penceresine](../ide/reference/output-window.md). Bu sembol olmadan hata ayıklama sınıfı yöntemleri derlenmemiş ve hiçbir çıktı oluşturulur. Bu simge hata ayıklama sürümünde tanımlanan ve yayın sürümünde tanımlı değil. Bir sürümde bu sembol tanımlama, programınızı yavaşlar gereksiz kod oluşturur.|  
|**TRACE sabitini tanımlayın**|Bu sembol tanımlama sağlayan çıkış işlevlerin koşullu derleme [izleme sınıfı](https://msdn.microsoft.com/library/system.diagnostics.trace.aspx). Bu simgeyle tanımlanan izleme sınıfı yöntemleri çıkışı Oluştur [çıkış penceresine](../ide/reference/output-window.md). Bu sembol olmadan izleme sınıfı yöntemleri derlenmemiş ve hiçbir izleme çıktısına oluşturulur. Bu simge, hem hata ayıklama ve yayın sürümleri için varsayılan olarak tanımlanır.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklayıcısı Ayarları ve Hazırlığı](../debugger/debugger-settings-and-preparation.md)



