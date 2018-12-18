---
title: Açma ve proje öğeleri kaydetme | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], file persistence
- files [Visual Studio], opening and saving
- editors [Visual Studio SDK], file persistence
ms.assetid: f71898ad-335f-4c43-a177-4da87078afd1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 895306a70d386b7a895b52b22704ec42a07d17ce
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31130608"
---
# <a name="opening-and-saving-project-items"></a>Açıp kaydederek proje öğeleri
Yeni bir proje türü eklediğinizde, projeler dosyalarınızda kaydetme ve açma yönetmelisiniz [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tümleşik geliştirme ortamı (IDE). Aşağıdaki konular, dosyaları açma ve kaydetme için farklı yaklaşımlara tartışın.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Dosya Aç Komutunu Kullanarak Dosyaları Görüntüleme](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)  
 IDE nasıl işlediği hakkında ile ilgili adım adım bir açıklama sağlar **açık dosya** komutu ve bu komutuna yanıt olarak projeleri rol.  
  
 [Birlikte Aç Komutunu Kullanarak Dosyaları Görüntüleme](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)  
 IDE nasıl işlediğini bir ayrıntılı, adım adım açıklama sağlar **birlikte Aç** bazı standart düzenleyicileri seçimine sahip bir dosyayı açma isteyen komutu.  
  
 [Nasıl Yapılır: Projeye Özgü Düzenleyicileri Açma](../../extensibility/how-to-open-project-specific-editors.md)  
 Projenizdeki belirli bir türdeki dosyaları bir projeye özgü Düzenleyicisi'ni kullanarak açılmalıdır belirtmek için adım adım yönergeler sağlar.  
  
 [Nasıl Yapılır: Standart Düzenleyicileri Açma](../../extensibility/how-to-open-standard-editors.md)  
 Proje türünüz dosyaları için standart bir düzenleyici açmak IDE etkinleştirme belirtmek için adım adım yönergeler sağlar.  
  
 [Nasıl Yapılır: Açık Belgeler için Düzenleyicileri Açma](../../extensibility/how-to-open-editors-for-open-documents.md)  
 Açık bir dosya için bir proje özgü düzenleyici açmak için adım adım yönergeler sağlar.  
  
 [Standart Belge Kaydetme](../../extensibility/internals/saving-a-standard-document.md)  
 IDE nasıl işlediği hakkında ile ilgili ayrıntılı bir açıklama sağlar **kaydetmek**, **Kaydet**, ve **Tümünü Kaydet** komutları bir belge için bir standart Düzenleyicisi'nde açılır.  
  
 [Özel Belge Kaydetme](../../extensibility/internals/saving-a-custom-document.md)  
 Bir diyagram ve IDE nasıl işlediğini konusunda ayrıntılı bilgi sağlar **kaydetmek**, **Kaydet**, ve **Tümünü Kaydet** komutları belgeler için özel bir düzenleyici açılır.  
  
 [Projedeki Bir Dosyayı Hangi Düzenleyicinin Açacağını Belirleme](../../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)  
 IDE uygun Düzenleyicisi'ni veya bir dosya için tasarımcı seçmek için aşağıdaki ele alınmaktadır.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Özel Düzenleyiciler ve Tasarımcılar Oluşturma](../../extensibility/creating-custom-editors-and-designers.md)  
 IDE barındırabilir ve her Düzenleyici açıklamalarını verir düzenleyicileri dört türlerini listeler.  
  
 [Proje Türleri](../../extensibility/internals/project-types.md)  
 Nasıl projeleri kod derlenmiş ve yerleşik şeklini denetlemek, düzenleyiciler nasıl açıldığı ve proje öğeleri nasıl biçimlendirileceğini anlatılmaktadır.