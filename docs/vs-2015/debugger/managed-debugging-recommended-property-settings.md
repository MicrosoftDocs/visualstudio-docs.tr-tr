---
title: 'Yönetilen hata ayıklama: Önerilen özellik ayarları | Microsoft Docs'
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
helpviewer_keywords:
- debugging [Visual Studio], managed
- debugging managed code, recommended property settings
ms.assetid: 3d14a8d4-2925-44d0-be41-ec546d411db9
caps.latest.revision: 32
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6c82a624e5a2847da5c0f85a9e2ef4180a338a34
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51724701"
---
# <a name="managed-debugging-recommended-property-settings"></a>Yönetilen Hata Ayıklama: Önerilen Özellik Ayarları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bazı özellikler tüm yönetilen hata ayıklama senaryoları için aynı şekilde ayarlamanız gerekir.  
  
 Aşağıdaki tablolarda, önerilen özellik ayarları gösterilmiştir.  
  
 Burada listelenmeyen ayarlar, farklı yönetilen proje türleri arasında değişebilir. Örneğin, **başlatma eylemi** kıyasla Windows Forms projesinde farklı şekilde ayarlanacak bir [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] proje.  
  
### <a name="configuration-properties-on-the-build-c-or-compile-visual-basic-tab"></a>Derleme (C#) veya derleme (Visual Basic) sekmesindeki yapılandırma özellikleri  
  
|**Özellik adı**|**Ayarı**|  
|-----------------------|-----------------|  
|**DEBUG sabitini tanımlayın**|C#ve F#: onay kutusunu işaretli olarak ayarlayın. Bu, uygulamanızın hata ayıklama sınıfını kullanmasına olanak tanır.|  
|**TRACE sabitini tanımlayın**|C#ve F#: onay kutusunu işaretli olarak ayarlayın. Bu, uygulamanızın izleme sınıfını kullanmasına olanak tanır.|  
|**Kodu En İyileştir**|C#, F#ve Visual Basic: false olarak ayarlayın. Oluşturulan yönergeler doğrudan sizin kaynak kodunuza karşılık gelmediğinden en iyi duruma getirilmiş kod hatalarını ayıklamak için zordur. Programınızda, yalnızca en iyi duruma getirilmiş kodda görüntülenen bir hata bulursanız, bu ayarı açabilirsiniz, ancak gösterilen kodun **ayrıştırılmış kodu** penceresi kodunda gördüğünüz eşleşmeyebilir en iyi duruma getirilmiş kaynaktan oluşturulur Düzenleyici. En iyi duruma getirilmiş kodda hata ayıklamak için devre dışı bırakmalısınız [yalnızca kendi kodum](just-my-code.md).<br /><br /> Daha fazla bilgi için [C# hata ayıklama yapılandırmaları için proje ayarları](../debugger/project-settings-for-csharp-debug-configurations.md) veya [Visual Basic hata ayıklama yapılandırması proje ayarları](../debugger/project-settings-for-a-visual-basic-debug-configuration.md).|  
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



