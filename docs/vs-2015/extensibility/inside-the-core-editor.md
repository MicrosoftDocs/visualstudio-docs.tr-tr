---
title: İçinde çekirdek Düzenleyicisi | Microsoft Docs
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
- editors [Visual Studio SDK], legacy - core editor
ms.assetid: 8265f31c-c45b-4858-882c-6d9f1e3b9083
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9aca4bb8ad55dbd4cac0a6f899731711ccb6db8f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51798553"
---
# <a name="inside-the-core-editor"></a>Çekirdek Düzenleyicisi içinde
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Çekirdek Düzenleyicisi değiştirebilir ve sorgu metin tabanlı bilgiler sağlayan çeşitli bileşenleri kümesidir. Eski API'yi kullanarak çekirdek Düzenleyici özelleştirdiyseniz, düzenleyici bağdaştırıcıları fabrikamserverpool'a yönlendirilebilir bu özelleştirmeler kullanmaya devam edebilir. Bu, ancak yeni bir düzenleyici API özelleştirmelerinizi uyum önerilir.  
  
 Çekirdek Düzenleyici önemli bazı yönleri şunlardır:  
  
-   Metin arabelleği  
  
-   Metin görünümü  
  
-   Kod penceresi  
  
-   Metin işaretçileri  
  
-   Metin Yöneticisi  
  
-   Dil Hizmetleri ile tümleştirme  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Eski API'yi Kullanarak Temel Düzenleyiciyi Başlatma](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)  
 Nasıl kullanılacağını hakkında adım adım yönergeler sağlar <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> Düzenleyici çekirdek örneğini oluşturmak için.  
  
 [Eski API'yi Kullanarak Metin Arabelleğine Erişme](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)  
 Çekirdek Düzenleyici içindeki metin arabelleği rolü açıklar, arabellek erişmek için kullanılır ve metin arabelleği nesne tarafından uygulanan arabirimler listesini sağlayan ilişkili sistemleri açıklanmaktadır <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>.  
  
 [Eski API'deki Metin Arabelleği Olayları](../extensibility/text-buffer-events-in-the-legacy-api.md)  
 Metin arabelleği olay bildirimi için kullanılan arabirimlerin listesini sağlar.  
  
 [Nasıl Yapılır: Eski API ile Metin Arabelleği Olaylarına Kaydolma](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)  
 Metin arabelleği olayları için öneri açıklar.  
  
 [Genel Ayarları İzlemek İçin Metin Yöneticisini Kullanma](../extensibility/using-the-text-manager-to-monitor-global-settings.md)  
 Metin Yöneticisi ile çekirdek Düzenleyicisi bileşenleri genel tercih bilgi paylaşımı için nasıl kullanıldığını ve metin Yöneticisi olaylarını bildirim almak nasıl ele alır.  
  
 [Eski API'yi Kullanarak Metin Görünümüne Erişme](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)  
 Çekirdek Düzenleyici içindeki metin görünümün rolü açıklar ve tarafından uygulanan arabirimler listeler <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> nesne.  
  
 [Eski API'yi Kullanarak Kod Penceresini Özelleştirme](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)  
 Nasıl bir kod penceresinde metin görünümünü içine almak için kullanılan, kod penceresi Yöneticisi kod penceresine süslemeleri sağlamak için nasıl kullanıldığını açıklar ve bildirim yeni bir görünüm sağlar hakkında bilgi sağlar.  
  
 [Eski API'yi Kullanarak Görünüm Ayarlarını Değiştirme](../extensibility/changing-view-settings-by-using-the-legacy-api.md)  
 Görünüm ayarları zorlamak ve zorunlu ayarlarını kaldırmak hakkında adım adım yönergeler sağlar.  
  
 [Dil Hizmetleri ve Temel Düzenleyici](../extensibility/language-services-and-the-core-editor.md)  
 Bir denetim kodu süslemeleri için dil hizmeti örneğinin açıklar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [İzlenecek Yol: Temel Düzenleyici Oluşturma ve Düzenleyici Dosya Türü Kaydetme](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)  
 Yönetilen koddan çekirdek Düzenleyici başlama hakkında adım adım yönergeler sağlar.  
  
 [Aşağı Açılan Çubuk](../extensibility/drop-down-bar.md)  
 Açılan çubuğunun nasıl kod penceresinde kullanılır ve bir açılan çubuğu uygularken kullanılan arabirimler açıklanmaktadır açıklanır.  
  
 [Eski API ile Metin İşaretçilerini Kullanma](../extensibility/using-text-markers-with-the-legacy-api.md)  
 Metin işaretçileri ve çekirdek Düzenleyicisi'nde nasıl kullanılacağını kavramını açıklar ve erişmek ve metin işaretçileri yönetmek için kullanılan arabirimleri listeler.  
  
 [Nasıl Yapılır: Standart Metin İşaretçileri Ekleme](../extensibility/how-to-add-standard-text-markers.md)  
 Bir metin işaretçisi oluşturmak ve özel komut için kısayol menüsü ekleme hakkında adım adım yönergeler sağlar.  
  
 [Nasıl yapılır: Özel Metin İşaretçileri Oluşturma](../extensibility/how-to-create-custom-text-markers.md)  
 Bir özel metin işaretçisi oluşturmak ve hizmet olarak işaret türü sağlamak hakkında adım adım yönergeler sağlar.

