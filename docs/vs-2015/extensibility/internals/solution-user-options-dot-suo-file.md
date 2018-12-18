---
title: Çözüm kullanıcı seçenekleri (. Suo) dosyası | Microsoft Docs
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
- .suo files, VSPackages
- suo files, VSPackages
- solutions, .suo files
- solutions, user options
- solution user options (.suo) file
ms.assetid: 75258e0d-600d-4a3d-94f4-3d7ac12cb47c
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f101f4efe0afe2132477b83731871872fdfc90c9
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51799859"
---
# <a name="solution-user-options-suo-file"></a>Çözüm Kullanıcı Seçenekleri (.Suo) Dosyası
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Çözüm kullanıcı seçenekleri (. suo) dosyası kullanıcı çözüm seçenekleri içerir. Bu dosya kaynak kodu denetimine iade.  
  
 Çözüm kullanıcı seçenekleri (. suo) dosyası, bir yapılandırılmış depolama veya bileşik, ikili biçimde depolanmış dosyasının örneğidir. Kullanıcı bilgilerini akışları .suo dosya bilgileri tanımlamak için kullanılan anahtarı olan akış adıyla kaydedin. Çözüm kullanıcı seçenekleri dosyası kullanıcı tercih ayarlarını depolamak için kullanılır ve Visual Studio çözüm kaydettiğinde otomatik olarak oluşturulur.  
  
 Ortam .suo dosya açıldığında, tüm yüklü VSPackages numaralandırır. VSPackage uyguluyorsa <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> arabirimi sonra ortamı çağrıları <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.LoadUserOptions%2A> VSPackage onu isteyen tüm verilerini .suo dosyasından yükleme yöntemi.  
  
 Bu, ne akışları bilmek VSPackage'nın sorumluluk .suo dosyasına yazılmış olur. Yazdığı her akış için VSPackage çağrılar geri ortamı üzerinden <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> Akış adı olan anahtar tarafından tanımlanan belirli bir akış yüklenemedi. Ortamı daha sonra geri akış adını geçirerek bu belirli akışını okumak için VSPackage çağırır ve bir `IStream` işaretçisine <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> yöntemi.  
  
 Bu noktada, başka bir çağrı yapılır `LoadUserOptions` .suo dosyasının okunması gereken başka bir bölüme olup olmadığını görmek için. Bu işlem, tüm veri akışlarını .suo dosya okunan ve ortamı tarafından işlenen kadar devam eder.  
  
 Çözüm zaman kaydedilmez veya kapalı, ortam çağrıları <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.SavePackageSolutionProps%2A> yöntemi için bir işaretçi ile <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.SaveUserOptions%2A> yöntemi. Bir `IStream` kaydedilecek ikili bilgiyi içeren geçirildiğinde <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.WriteUserOptions%2A> çağrıları ve .suo dosya bilgileri ardından yazan yöntemi `SaveUserOptions` yeniden başka bir akış yazmak için .suo bilgilerinin olup olmadığını görmek için yöntemi dosya.  
  
 Bu iki yöntem `SaveUserOptions` ve `WriteUserOptions`, .suo dosya işaretçisi olarak geçirerek, kaydedilecek bilgi her akış için yinelemeli olarak adlandırılan `IVsSolutionPersistence`. Bunlar, .suo dosya için birden çok akış yazılmasını izin vermek için yinelemeli olarak adlandırılır. Bu şekilde, kullanıcı bilgilerini çözümde kalıcı hale ve çözüm bir sonraki açılışında olması garanti edilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>   
 [Çözümler](../../extensibility/internals/solutions.md)

