---
title: İstemci tarafı betikte hata ayıklama | Microsoft Docs
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
- debugging [Visual Studio], client-side scripts
- client-side scripts, debugging
ms.assetid: bb668527-2288-47bd-a6c8-cecbad76dde2
caps.latest.revision: 33
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3aa04ab77b6e3dc6264a517c83c4ed319f36d686
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51817808"
---
# <a name="client-side-script-debugging"></a>İstemci Tarafı Betikte Hata Ayıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio hata ayıklayıcı, bulma ve ASP.NET sayfaları istemci tarafı betiklerde hataları düzeltmek için kapsamlı bir hata ayıklama ortamı sağlar.  
  
## <a name="opening-script-documents"></a>Komut dosyası belgeleri açma  
 Sunucu tarafı ve istemci tarafı komut dosyası belgeleri listesini görebilirsiniz **Çözüm Gezgini** görüntülemek için. Herhangi bir betik belgeden açabileceğiniz **Çözüm Gezgini**. Daha fazla bilgi için [nasıl yapılır: betik belgelerini görüntüleme](../debugger/how-to-view-script-documents.md).  
  
## <a name="breakpoint-mapping"></a>Kesme noktası eşleme  
 Visual Studio'da, sunucu tarafı kodu doğrudan hata ayıklaması yapılamıyor, ancak bir sunucu tarafı dosyasında bir kesme noktası ayarlayabilirsiniz. Visual Studio otomatik olarak istemci tarafındaki dosyada karşılık gelen bir konuma kesme noktası eşler ve istemci tarafındaki kodda eşlenmiş bir kesme noktası oluşturur.  
  
## <a name="manually-or-automatically-attaching-to-script"></a>El ile veya otomatik olarak komut dosyasına ekleme  
 Betikte hata ayıklamayı başlatmak için [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], hata ayıklayıcının hata ayıklamak istediğiniz komut dosyasına iliştirilmesi gerekir. El ile veya otomatik olarak bu durum oluşabilir.  
  
 Kullanarak el ile ekleyebilirsiniz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] eklemek istediğiniz çalışan bir komut dosyası işlemini seçmek için hata ayıklayıcı arabirim. Daha fazla bilgi için [nasıl yapılır: betiğe ekleme](../debugger/how-to-attach-to-script.md).  
  
 Aşağıdaki şeylerden biri meydana geldiğinde hata ayıklayıcı komut dosyasına otomatik olarak ekler:  
  
- Komut dosyasında bir kesme noktasına gidersiniz.  
  
- Bir VBScript `Stop` deyimi veya JScript `debugger` betik kodunuzu deyiminde.  
  
- Tarayıcı veya sunucu bir söz dizimi karşılaşır veya betiğinizde çalıştırma hatası. Bu durumda, bir iletişim kutusu görünür ve hata ayıklamayı başlatmak için seçeneğiniz vardır.  
  
  El ile betiğe ekleme, betik işlem şekilde durduruluncaya kadar çalışmaya devam eder. Seçerek durdurabilirsiniz **sonu** üzerinde **hata ayıklama** menüsü.  
  
  Hata ayıklayıcı otomatik olarak ekler, satırında komut dosyası yürütme durdurulur nerede kesme noktası `Stop` deyimi veya `debugger` ifadesinin veya hatanın oluştuğu veya Internet Explorer'da hata ayıklamayı başlatmayı seçtiğiniz noktada.  
  
  Bu noktada, hata ayıklamayı başlatmak için normal hata ayıklayıcı tesislerini kullanabilirsiniz. Örneğin, kullanabileceğiniz **adım** satır satır kodunuzu yürütmeye devam etmek için komutları. Kullanabileceğiniz **çağrı yığını** komut akışını görüntülemek ve denetlemek için penceresi. Değişken pencerelerini kullanabilirsiniz veya **hemen** penceresi değişkenleri ve özellikleri görüntülemek veya değiştirmek için.  
  
## <a name="enhanced-error-messages-for-script-debugging"></a>Betik hata ayıklama için geliştirilmiş hata iletileri  
 Visual Studio genel betik hata ayıklama sorunları için Gelişmiş hata iletileri sağlar. Internet Explorer'ı el ile eklemediğiniz sürece bu iletiler görüntülenmez. Internet Explorer otomatik olarak açıldığında bir hata koşuluyla karşılaşırsanız, hata iletilerini görebilmeniz için el ile eklemeyi deneyin.  
  
## <a name="debugging-ajax-script-applications"></a>AJAX komut dosyası uygulamalarının hatalarını ayıklama  
 AJAX etkinleştirilmiş Web uygulamaları, komut dosyası kodunu yoğun kullanmasına ve özel hata ayıklama zorluklarına neden olur. AJAX hata ayıklama teknikleri hakkında daha fazla bilgi için bkz.  
  
 [Hata ayıklama ve Ajax uygulamalara genel bakış izleme](http://msdn.microsoft.com/library/92684ea0-7bb4-4a34-9203-3aa6394ce375).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ASP.NET ve AJAX uygulamalarında hata ayıklama](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Betik hata ayıklamasında sınırlamalar](../debugger/limitations-on-script-debugging.md)   
 [Değişken Windows](http://msdn.microsoft.com/library/ce0a67f6-2502-4b7a-ba45-cc32f8aeba3e)   
 [Komut penceresi](../ide/reference/immediate-window.md)   
 [Hata ayıklama ve izleme Ajax uygulamalara genel bakış](http://msdn.microsoft.com/library/92684ea0-7bb4-4a34-9203-3aa6394ce375)



