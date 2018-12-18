---
title: 'Nasıl yapılır: dosyaları kaydetme ve açma kodlamayla | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Unicode, bi-directional language support
- files, encoding
- bi-directional language support, encoded files
- file encoding, bi-directional languages
ms.assetid: cb52b732-b395-4ba1-a3ef-104b3942a12a
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b179637d9607db70aac415abd477da4a62852efe
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49213791"
---
# <a name="how-to-save-and-open-files-with-encoding"></a>Nasıl Yapılır: Dosyaları Kodlamayla Kaydetme ve Açma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dosyaları belirli karakter çift yönlü dil desteği için kodlama ile kaydedebilirsiniz. Ayrıca, böylece Visual Studio dosyayı doğru görüntüler bir dosyayı açtığınızda kodlama belirtebilirsiniz.  
  
### <a name="to-save-a-file-with-encoding"></a>Dosya kodlama ile kaydetmek için  
  
1.  Gelen **dosya** menüsünde seçin **dosyayı farklı Kaydet**ve yanındaki açılan düğmeyi'ye tıklayın **Kaydet** düğmesi.  
  
     **Gelişmiş kaydetme seçenekleri** iletişim kutusu görüntülenir.  
  
2.  Altında **kodlama**, dosya için kullanılacak kodlama seçin.  
  
3.  İsteğe bağlı olarak, altında **satır sonlarını**, satır sonu karakterleri için biçimi seçin.  
  
     Bu seçenek dosyayı farklı bir işletim sistemi kullanıcılarla alışverişi yapmak istiyorsanız yararlıdır.  
  
     Belirli bir biçimde kodlandı bildiğiniz bir dosyayla çalışmak istiyorsanız, Visual Studio kodlama dosyası açılırken kullanılacak söyleyebilirsiniz. Kullandığınız yöntem, dosyanın, projenizin bir parçası olmasına göre değişir.  
  
### <a name="to-open-an-encoded-file-that-is-part-of-a-project"></a>Bir projenin parçası olan kodlanmış bir dosyayı açmak için  
  
1.  İçinde **Çözüm Gezgini**, dosyaya sağ tıklayın ve seçin **birlikte Aç**.  
  
2.  İçinde **birlikte Aç** iletişim kutusunda, dosyayı açmak için bir düzenleyici seçin.  
  
     Form Düzenleyicisi gibi birçok Visual Studio düzenleyicileri kodlamasını Otomatik Algıla ve uygun şekilde dosyasını açın. Bir kodlama seçmenize olanak tanıyan bir düzenleyici seçerseniz **kodlama** iletişim kutusu görüntülenir.  
  
3.  İçinde **kodlama** iletişim kutusunda, düzenleyici kullanması gereken kodlama seçin.  
  
### <a name="to-open-an-encoded-file-that-is-not-part-of-a-project"></a>Bir projenin parçası değil kodlanmış bir dosyayı açmak için  
  
1.  Üzerinde **dosya** menüsünde **açın**, seçin **dosya** veya **Web'den dosya**ve ardından dosyayı açmak için seçin.  
  
2.  Yanındaki açılan düğmeyi tıklayın **açık** düğmesini tıklatın ve seçin **birlikte Aç**.  
  
3.  Adım 2 ve 3 önceki yordamı izleyin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kodlama ve Windows Forms Genelleştirme](http://msdn.microsoft.com/library/22e8965d-a712-42b3-8167-3ee346bd70f9)   
 [Uygulamaları Genelleştirme ve Yerelleştirme](../ide/globalizing-and-localizing-applications.md)

