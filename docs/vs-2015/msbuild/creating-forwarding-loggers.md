---
title: İletme Günlükçüleri oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MSBuild, forwarding loggers
- MSBuild, logging
ms.assetid: 3aebf9c8-b62c-4cb2-b2d6-8cdfcd369a24
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 46cff57e8238e00f914f8437fbc81d1887e7d629
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49281248"
---
# <a name="creating-forwarding-loggers"></a>İletme Günlükçüleri Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
İletme günlükçüleri çok işlemcili bir sistemde projeler derlerken izlemek istediğiniz olayları seçin vererek günlük verimliliği artırın. İletme günlükçüleri etkinleştirerek merkezi Günlükçü aşırı yüklenilmesini, derleme zamanı yavaşlatmasını ve günlüğünüzün yığılmak istenmeyen olayları engelleyebilirsiniz.  
  
 Bir iletme Günlükçü oluşturmak için her iki uygulama olabilir. <xref:Microsoft.Build.Framework.IForwardingLogger> arabirim ve kendi yöntemlerini el ile uygulama veya kullanın <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger> sınıf ve onun önceden yapılandırılmış yöntemleri. (İkincisi çoğu uygulama için yeterli olacaktır.)  
  
## <a name="register-events-and-respond-to-them"></a>Kayıt olayları ve bunlara yanıt  
 Birden çok işlemcili sistem üzerinde bir derleme sırasında ana yapı işlemi tarafından oluşturulan bir alt işlem ikincil derleme altyapısı tarafından bildirilen bir iletme Günlükçü derleme olayları hakkında bilgi toplar. Ardından, verdiğiniz yönergelere dayalı, Orta Günlükçü iletmek için olayları iletme Günlükçü seçer.  
  
 İletme günlükçüleri izlemek istediğiniz olayları işlemek için kaydetmeniz gerekir. Etkinliklere kaydolmak için günlükçüleri kılmalı <xref:Microsoft.Build.Utilities.Logger.Initialize%2A> yöntemi. Bu yöntem artık isteğe bağlı bir parametre içeren `nodecount`, ayarlanabilecek işlemci sayısını sistemde. (Varsayılan değer 1'dir.)  
  
 Olayları izlemek için kullanabileceğiniz örnekler <xref:Microsoft.Build.Framework.IEventSource.TargetStarted>, <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted>, ve <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished>.  
  
 Birden çok işlemcili ortamda, düzensiz alınabilmesi olay iletileri olasıdır. Bu nedenle, olay işleyicisi iletme Günlükçü kullanarak olayları Değerlendirmeli ve iletmek üzere merkezi günlükçüyü yeniden yönlendirici'ye geçirmek için hangi olayları belirlemek üzere program. Bunu gerçekleştirmek için kullanabileceğiniz <xref:Microsoft.Build.Framework.BuildEventContext> sınıfı, iletmek istediğiniz olayları tanımlamaya yardımcı olmak için her ileti için ekli olduğu ve ardından olaylara adlarını geçirin <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger> sınıfı (veya bir öğesinin). Bu yöntemi kullandığınızda, diğer belirli kodlama olayları gerekli değildir.  
  
## <a name="specify-a-forwarding-logger"></a>Bir iletme Günlükçü belirtin  
 İletme Günlükçü derlemeye derlendikten sonra söylemelisiniz [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] yapılar sırasında kullanılacak. Bunu yapmak için `/FileLogger`, `/FileLoggerParameters`, ve `/DistributedFileLogger` MSBuild.exe ile birlikte anahtarlar. `/FileLogger` Günlükçü doğrudan bağlı olduğu anahtar MSBuild.exe söyler. `/DistributedFileLogger` Anahtar, düğüm başına bir günlük dosyası olduğu anlamına gelir. Parametreleri iletme Günlükçü üzerinde ayarlamak için kullanın `/FileLoggerParameters` geçin. Bunlar ve diğer MSBuild.exe anahtarlar hakkında daha fazla bilgi için bkz. [komut satırı başvurusu](../msbuild/msbuild-command-line-reference.md).  
  
## <a name="multi-processor-aware-loggers"></a>Birden çok işlemciye duyarlı günlükçüler  
 Çok işlemcili bir sistemde bir proje oluşturduğunuzda, her işlemci derleme iletilerden otomatik olarak birleştirilmiş bir dizisinde, araya eklemeli değil. Bunun yerine, bir ileti önceliği kullanarak gruplandırma kurmak <xref:Microsoft.Build.Framework.BuildEventContext> her iletiye sınıfı. Birden çok işlemcili oluşturma hakkında daha fazla bilgi için bkz. [çok işlemcili ortamda oturum açma](../msbuild/logging-in-a-multi-processor-environment.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Derleme günlükleri alma](../msbuild/obtaining-build-logs-with-msbuild.md)   
 [Günlükçüleri derleme](../msbuild/build-loggers.md)   
 [Birden Çok İşlemcili Ortamda Oturum Açma](../msbuild/logging-in-a-multi-processor-environment.md)



