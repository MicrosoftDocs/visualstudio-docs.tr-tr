---
title: Önerilen özellik ayarları için hata ayıklayıcı C#, VB | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], managed
- debugging managed code, recommended property settings
ms.assetid: 3d14a8d4-2925-44d0-be41-ec546d411db9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 69b98fe00301ad9230cb4f560a0a1d9dc1d3922f
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53064964"
---
# <a name="managed-debugging-recommended-property-settings"></a>Yönetilen Hata Ayıklama: Önerilen Özellik Ayarları
Bazı özellikler tüm yönetilen hata ayıklama senaryoları için aynı şekilde ayarlamanız gerekir.  
  
 Aşağıdaki tablolarda, önerilen özellik ayarları gösterilmiştir.  
  
 Burada listelenmeyen ayarlar, farklı yönetilen proje türleri arasında değişebilir. Örneğin, **başlatma eylemi** kıyasla Windows Forms projesinde farklı şekilde ayarlanacak bir [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] proje.  
  
### <a name="configuration-properties-on-the-build-c-or-compile-visual-basic-tab"></a>Derleme (C#) veya derleme (Visual Basic) sekmesindeki yapılandırma özellikleri  
  
|**Özellik adı**|**Ayarı**|  
|-----------------------|-----------------|  
|**DEBUG sabitini tanımlayın**|C#ve F#: onay kutusunu işaretli olarak ayarlayın. Bu, uygulamanızın hata ayıklama sınıfını kullanmasına olanak tanır.|  
|**TRACE sabitini tanımlayın**|C#ve F#: onay kutusunu işaretli olarak ayarlayın. Bu, uygulamanızın izleme sınıfını kullanmasına olanak tanır.|  
|**Kodu En İyileştir**|C#, F#ve Visual Basic: false olarak ayarlayın. Oluşturulan yönergeler doğrudan sizin kaynak kodunuza karşılık gelmediğinden en iyi duruma getirilmiş kod hatalarını ayıklamak için zordur. Programınızda, yalnızca en iyi duruma getirilmiş kodda görüntülenen bir hata bulursanız, bu ayarı açabilirsiniz, ancak gösterilen kodun **ayrıştırılmış kodu** penceresi kodunda gördüğünüz eşleşmeyebilir en iyi duruma getirilmiş kaynaktan oluşturulur Düzenleyici. En iyi duruma getirilmiş kodda hata ayıklamak için yalnızca kendi Kodum'u kapatmanız gerekir. (Bkz [Adımlamayı yalnızca kendi kodum kısıtlama](../debugger/navigating-through-code-with-the-debugger.md#BKMK_Restrict_stepping_to_Just_My_Code)).<br /><br /> Daha fazla bilgi için [C# hata ayıklama yapılandırmaları için proje ayarları](../debugger/project-settings-for-csharp-debug-configurations.md) veya [Visual Basic hata ayıklama yapılandırması proje ayarları](../debugger/project-settings-for-a-visual-basic-debug-configuration.md).|  
|**Çıkış yolu**|Ayarlamak için bin\Debug\\.|  
|**Gelişmiş derleme seçenekleri**|Yalnızca Visual Basic. Tıklayın **Gelişmiş** aşağıdaki tabloda açıklanan Gelişmiş özellikleri ayarlamak için.|  
  
### <a name="advanced-compiler-settings-dialog-box"></a>Gelişmiş Derleyici Ayarları iletişim kutusu  
  
|**Özellik adı**|**Ayarı**|  
|-----------------------|-----------------|  
|**Eniyileştirmeleri etkinleştir**|Belirtilen nedenlerden dolayı false olarak ayarlanmış **kodu En İyileştir** önceki tabloda seçeneği.|  
|**Hata ayıklama bilgileri üret**|Bu onay derlerken, ayarlanacak/Debug bayrağının hata ayıklamayı kolaylaştırmak için gereken bilgileri oluşturan kutusunu seçin.|  
|**DEBUG sabitini tanımlayın**|Tanımlamak için bu onay kutusunu işaretleyin `DEBUG` kullanmak için uygulamanızı sağlayan sabiti <xref:System.Diagnostics.Debug> sınıfı.|  
|**TRACE sabitini tanımlayın**|Tanımlamak için bu onay kutusunu işaretleyin `TRACE` kullanmak için uygulamanızı sağlayan sabiti <xref:System.Diagnostics.Trace> sınıfı.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yönetilen kodda hata ayıklama](../debugger/debugging-managed-code.md)   
 [C#, F# ve Visual Basic Proje Türleri](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)