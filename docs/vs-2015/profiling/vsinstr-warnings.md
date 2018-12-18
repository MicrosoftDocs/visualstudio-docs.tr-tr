---
title: Vsınstr uyarıları | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- instrumentation, VSInstr tool
- warnings
- VSInstr tool
- warnings, VSInstr tool
- performance tools, VSInstr tool
ms.assetid: 47512bc9-a8e9-4628-883a-d9888edab786
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: be30404e4fb9cff6c53bb3afbdedb4ce03ba2d80
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51765132"
---
# <a name="vsinstr-warnings"></a>VSInstr Uyarıları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aşağıdaki tabloda VSInstr.exe araç tarafından verilen uyarılarını listeler. Uyarıyı görüntülenmesini engellemek için uyarı numaralarını NOWARN seçeneğiyle kullanabilirsiniz.  
  
|Uyarı numarası|Açıklama|  
|--------------------|-----------------|  
|**VSP2000**|İç Hata. Bu yürütülebilir dosya için modülün dosya adı alınamıyor.|  
|**VSP2001**|\<derleme adı > kesin adlandırılmış bir derlemedir. Yürütülmek üzere önce onu yeniden imzalanması gerekir.<br /><br /> İmzalı bir derleme işaretlenmiş durumda olduğunda bu uyarı oluşur. İkili çekilmeye veya geçici olarak devre dışı tanımlayıcı ad gereksinim kapatmak için sn.exe Aracı'nı kullanabilirsiniz. Daha fazla bilgi için [Sn.exe (tanımlayıcı ad aracı)](http://msdn.microsoft.com/library/c1d2b532-1b8e-4c7a-8ac5-53b801135ec6).|  
|**VSP2002**|İşlevi bulunamadı \<funcname > dosyasındaki \<dosya adı ><br /><br /> Bir işlev içinde belirtilen dosya bulunamıyorsa, bu uyarı oluşur.|  
|**VSP2003**|Çapraz atlama işlevi bulunamadı \<funcname > dosyasındaki \<dosya adı >.<br /><br /> Vsınstr silinmez olamaz, bu uyarı, çapraz atlar meydana gelir. Çapraz atlama kodu iyileştirme için kullanılır.|  
|**VSP2004**|İşlev \<funcname > EXCLUDE komut satırı anahtarı kullanılarak dışlandı ancak çapraz atlama içerdiği için gerekli.<br /><br /> İşlevi, hariç TUTMA seçeneğini kullanarak dışlandı ancak izleme işlemi sırasında gerekli bu uyarı oluşur. Profil Oluşturucu otomatik olarak gerekli işlevi içerir.|  
|**VSP2005**|İç izleme hatası \<hata metni ><br /><br /> İzleme gerçekleştirdiyseniz, bu uyarı görüntülenir. Bunu düzeltilebilir olup olmadığını belirlemek için hata metni gözden geçirin.|  
|**VSP2006**|İçin PDB bulunamadı \<adı ><br /><br /> PDB dosyası arama yolunda yok veya ikili ile eşlemiyor değilse bu uyarı oluşur.|  
|**VSP2007**|\<Dosya adı > hiçbir izlenebilir kod içermiyor.<br /><br /> Bu uyarı, İşlevler ikili dosyadaki tüm dışlanan veya belirtilen dosya yalnızca kaynaklar içeriyorsa görüntülenir.|  
|**VSP2008**|Güvenlik öznitelikleri alınamıyor \<adı >. Hata kodu \<kod ><br /><br /> Kullanıcı READ_DAC iznine sahip değilse bu uyarı oluşur. İzleme işlemi sırasında profil oluşturucu için ikili dosya özgün DACL korumak çalışır. Özgün ikiliyi yeni bir ikili dosya ile değiştirilir olduğundan, özgün ikilinin DACL kopyalanır ve yeni ikili için uygulanır. Kullanıcı özgün iki READ_DAC erişim olmaması durumunda başarısız olabilir.|  
|**VSP2009**|Güvenlik öznitelikleri ayarlanamadı \<adı >. Hata kodu \<hata numarası ><br /><br /> Kullanıcı WRITE_DAC iznine sahip değilse bu uyarı oluşur. İzleme işlemi sırasında profil oluşturucu için ikili dosya özgün DACL korumak çalışır. Özgün ikiliyi yeni bir ikili dosya ile değiştirilir olduğundan, özgün ikilinin DACL kopyalanır ve yeni ikili için uygulanır. Kullanıcı yeni ikili dosya WRITE_DAC erişim olmaması durumunda başarısız olabilir.|  
|**VSP2010**|Hiçbir işlevlerdir özellikle /-EXCLUDE seçenekleri nedeniyle, - izleme için seçili içerir|  
|**VSP2011**|İçerme/dışlama funcspec \<adı > tüm işlevleri eşleşmiyor|  
|**VSP2012**|Görüntü için kod kapsamı izleme eklenmiş herhangi bir kod içermiyor.<br /><br /> Profiler, aşağıdaki kodun türünü izleme değil:<br /><br /> -Statik CRT işlevleri<br />-Yönetilen yöntemleri ile NonUserCodeAttribute öznitelikli<br />-DebuggerHiddenAttribute ile öznitelikli yönetilen yöntemleri<br />-MASM blokları<br /><br /> Bu filtreleme sonrasında, varsa, kod sol bu uyarı oluşturulur.|  
|**VSP2013**|Bu görüntüyü izlemek 32-bit işlem olarak çalıştırmayı gerektirir. CLR üst bilgi bayrakları bunu yansıtmak için güncelleştirildi.<br /><br /> Profil Oluşturucu, 64-bit işletim sistemlerinde WOW64 öykünücüsünde 32-bit işlem açabilmek ikili değiştirir. Var olan bir 64 bit işlemde yüklü olmaları durumunda kitaplıkları (DLL'ler) için bu başarısız olabilir. Bu uyarı, bağımlılık kullanıcıya bildirir.|  
|**VSP2014**|Elde edilen izleme eklenmiş görüntü geçersiz görünüyor ve çalışmayabilir.<br /><br /> Geçersiz PE üst bilgisi son kullanılan derleme sahip olduğunda bu ileti oluşur.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [VSInstr](../profiling/vsinstr.md)



