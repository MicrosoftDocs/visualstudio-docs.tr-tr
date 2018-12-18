---
title: Hata ayıklama yapılandırması proje ayarları bir VB | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vbProjectPropertiesDebug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- project settings [Visual Studio], debug configurations
- debug builds, project settings
- debugging [Visual Basic], debugger settings
- projects [Visual Studio], debug configurations
- project configurations, debug
- debug configurations, Visual Basic
ms.assetid: 72a8483a-af0b-4403-8b0d-ee9ad71ee435
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d70ec195418b46a022ca73d6ac3656de8e652f06
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53059697"
---
# <a name="project-settings-for-a-visual-basic-debug-configuration"></a>Visual Basic Hata Ayıklama Yapılandırması Proje Ayarları
Proje ayarlarını değiştirebilirsiniz bir [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] hata ayıklama yapılandırmasında **özellik sayfaları** anlatıldığı gibi penceresinde [hata ayıklama ve yayın yapılandırmaları](../debugger/how-to-set-debug-and-release-configurations.md). Aşağıdaki tablolarda, hata ayıklayıcı ile ilgili ayarların nerede bulunacağı gösterilmektedir **özellik sayfaları** penceresi.  
  
> [!WARNING]
>  Bu konu, UWP uygulamaları için geçerli değil. Bkz: [(VB, C#, C++ ve XAML) bir hata ayıklama oturumu başlatın](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)  
  
### <a name="debug-tab"></a>Hata ayıklama sekmesi  
  
| Ayar | Açıklama |
|------------------------------| - |
| **Yapılandırma** | Uygulama derlemek için modu ayarlar. Arasından seçim **etkin (hata ayıklama)**, **hata ayıklama**, **yayın**, **yapılandırmalarında**. |
| **Başlatma eylemi** | Bu grubu denetimleri, hata ayıklama menüsünden Başlangıç meydana gelir eylemi belirtir.<br /><br /> -   **Proje başlangıç** varsayılandır ve hata ayıklama için başlangıç projesi başlatır. <br />-   **Harici program Başlat** başlatmak ve olmayan bir programa ekledikten sağlayan parçası olan bir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] proje. Daha fazla bilgi için [çalışan işlemlere ekleme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).<br />-   **URL'de tarayıcı başlatmak** bir Web uygulaması ayıklamanızı sağlar. |
| **Komut satırı bağımsız değişkenleri** | Ayıklanacak programın komut satırı bağımsız değişkenlerini belirtir. Komut başlangıç dış program içinde belirtilen program adı addır. Başlatma eylemi için başlangıç URL'si olarak ayarlanırsa, komut satırı bağımsız değişkenleri göz ardı edilir. |
| **Çalışma dizini** | Ayıklanan programın çalışma dizini belirtir. İçinde [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], çalışma dizini uygulamayı başlatan dizindir. Varsayılan çalışma dizini, \bin\Debug veya geçerli yapılandırmasına bağlı olarak, \bin\Release bağlıdır. |
| **Uzak makine kullanma** | Uzaktan hata ayıklama, onay kutusu seçili olduğunda etkindir. Metin kutusunda, hata ayıklama amacıyla nerede uygulamanın çalışacağı uzak bir makine adını yazın veya bir [Msvsmon sunucu adı](../debugger/remote-debugging.md). Uzak makinede EXE konumunu derleme sekmesi çıkış yolu özelliği tarafından belirtilir. Konum, uzak makinede paylaşılabilir bir dizin olmalıdır. |
| **Yönetilmeyen kodda hata ayıklama** | Yerel (yönetilmeyen) Win32 koddaki çağrıları yönetilen uygulamanızın hatalarını ayıklamanızı sağlar. Bu hata ayıklayıcı türü için karma seçerek aynı etkiye sahip bir [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] proje. |
| **SQL Server hata ayıklama** | SQL Server veritabanı nesnelerini hata ayıklamasını sağlar. |
  
### <a name="compile-tab-press-advanced-compile-options-button"></a>Sekme derle: Gelişmiş derleme seçenekleri düğmesine basın  
  
| Ayar | Açıklama |
|---------------------------| - |
| **Eniyileştirmeleri etkinleştir** | Bu seçenek işaretinin kaldırılması gerekir. En iyi duruma getirme neden görünen kaynak kodundan farklı olacak şekilde gerçekte çalıştırılan kod [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]ve bu nedenle hata ayıklaması zor yapar. Kodun en iyilenmesi ise sembolleri olmayan yüklenemeyen varsayılan olarak yalnızca kendi kodum'hata ayıklama sırasında. |
| **Hata ayıklama bilgileri üret** | Varsayılan olarak, hem hata ayıklama ve yayın tarafından tanımlanan sürümleri, bu (/ debug derleyici seçeneği eşdeğer) ayarı oluşturur hata ayıklama bilgileri oluşturma zamanında. Hata ayıklayıcı, hata ayıklaması yapıyorsanız kullanışlı bir formda değişken adları ve diğer bilgileri göstermek için bu bilgileri kullanır. Programınızın bu bilgiler olmadan derleme yaparsanız, hata ayıklayıcı işlevselliği sınırlı olacaktır. Daha fazla bilgi için [/debug](/dotnet/visual-basic/reference/command-line-compiler/debug). |
| **DEBUG sabitini tanımlayın** | Bu sembol tanımlama sağlayan çıkış işlevlerin koşullu derleme [hata ayıklama sınıfı](/dotnet/api/system.diagnostics.debug). Tanımlanan bu simge ile hata ayıklama sınıfı yöntemleri çıkışı Oluştur [çıkış penceresine](../ide/reference/output-window.md). Bu sembol olmadan hata ayıklama sınıfı yöntemleri derlenmemiş ve hiçbir çıktı oluşturulur. Bu simge hata ayıklama sürümünde tanımlanan ve yayın sürümünde tanımlı değil. Bir sürümde bu sembol tanımlama, programınızı yavaşlar gereksiz kod oluşturur. |
| **TRACE sabitini tanımlayın** | Bu sembol tanımlama sağlayan çıkış işlevlerin koşullu derleme [izleme sınıfı](/dotnet/api/system.diagnostics.trace). Bu simgeyle tanımlanan izleme sınıfı yöntemleri çıkışı Oluştur [çıkış penceresine](../ide/reference/output-window.md). Bu sembol olmadan izleme sınıfı yöntemleri derlenmemiş ve hiçbir izleme çıktısına oluşturulur. Bu simge, hem hata ayıklama ve yayın sürümleri için varsayılan olarak tanımlanır. |
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklayıcısı Ayarları ve Hazırlığı](../debugger/debugger-settings-and-preparation.md)