---
title: 'DA0030: Veritabanı projeleri için katman etkileşim ölçümlerini Topla | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.DA0030
- vs.performance.rules.DA0030
- vs.performance.30
ms.assetid: 42b2f69d-0cfa-4854-82c4-589c3d8b4557
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0d0fb38348a901582182bdfaec2d7d775ec195f7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49814018"
---
# <a name="da0030-gather-tier-interaction-measurements-for-database-projects"></a>DA0030: veritabanı projeleri için katman etkileşim ölçümlerini Topla

|||  
|-|-|  
|Kural Kimliği|DA0030|  
|Kategori|Profil oluşturma araçları kullanım|  
|Profil oluşturma yöntemi|Örnekleme|  
|İleti|Çok katmanlı uygulamalar için etkileşim ölçümleri toplamayı veritabanı kullanım modellerini ve anahtar veri anlamanıza yardım gecikmeler erişir. Uygulama, katman etkileşim profili oluşturma seçeneği etkin yeniden profil oluşturmayı deneyin.|  
|Kural türü|Bilgiler|  

## <a name="cause"></a>Sebep  
 Çağrılar <xref:System.Data> yöntemlerdir profil oluşturma verilerinin önemli bir kısmı ve profil oluşturma çalışması katman etkileşim verileri toplanan değil. Katman etkileşim verileri ekleme ve yeniden profil oluşturmayı göz önünde bulundurun.  

## <a name="rule-description"></a>Kural açıklaması  
 Dahil olmak üzere System.Data ad alanlarında bulunan işlevlerinde önemli bir etkinlik olduğunda bu kural tetikler <xref:System.Data.Linq> <xref:System.Data.Linq>.  

 Çok katmanlı uygulamaların katmanlı Hizmetleri, sunu ve veri katmanları için kullanın. Genellikle veri katmanı, bir veritabanı yönetim sistemi gibi Microsoft SQL Server çalıştıran ayrı bir işlemdir. Veri katmanı da ayrı bir makinede uygulama geri kalanından çalışıyor olabilir. Örnekleme profil işlevleri ve işlem dışı çalışan hizmetler küçük bir anlayış sağlayın veya uzaktan.  

 Profil oluşturma araçları, çok katmanlı uygulamaların, zaman uyumsuz çağrıları ADO.NET hizmetleri kullanarak bir Microsoft SQL Server veri katmanı ile etkileşim için zamanlama bilgilerini toplayabilirsiniz. Katman etkileşim profili oluşturma açıkça etkinleştirmeniz gerekir. Varsayılan olarak açık değildir.  

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?  
 Bu kural yalnızca bilgi amaçlıdır ve düzeltici eylem gerekli değil.  

 Visual Studio IDE içinden veri profil oluşturma için katman etkileşim verileri ekleme hakkında daha fazla bilgi için bkz: [katman etkileşim verileri toplama](../profiling/collecting-tier-interaction-data.md). Komut satırından katman etkileşim verileri ekleme hakkında daha fazla bilgi için bkz: [katman etkileşim verileri toplama](../profiling/adding-tier-interaction-data-from-the-command-line.md).