---
title: 'Nasıl yapılır: Visual Studio çözümünün parçası olmayan yürütülebilir öğede hata ayıklama | Microsoft Docs'
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
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], executables
- executable files, importing
- executable files, debugging outside of projects
ms.assetid: 3ea176e8-1ce5-42c4-b7a2-abe3a2765033
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a7fb9b0a31f078ce197851bccb1f4c85f24408a0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51798670"
---
# <a name="how-to-debug-an-executable-not-part-of-a-visual-studio-solution"></a>Nasıl Yapılır: Visual Studio Çözümünün Parçası Olmayan Yürütülebilir Öğede Hata Ayıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bazen, hata ayıklama olmayan yürütülebilir bir dosya isteyebilirsiniz parçası olan bir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] proje. Oluşturduğunuz dışında bir yürütülebilir dosya olabilir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ya da başka birinden aldığınız bir çalıştırılabilir.  
  
 Visual Studio dışında yürütülebilir dosyayı başlatmak ve onu kullanarak eklemek için bu sorunun her zamanki yanıtı olan [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] hata ayıklayıcı. Daha fazla bilgi için[çalışan işlemlere ekleme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
 Bir uygulamaya eklemek, birkaç saniye sürer, bazı adımları el ile gerektirir. Bu gecikme, başlatma sırasında oluşan bir sorunu çözmeye çalışıyorsanız, eklemenin yardımcı olmayacağı olduğunu gösterir. Ayrıca, kullanıcı girişini beklemeyen ve hızlı şekilde biten bir program ayıklıyorsanız, buna eklemek için zaman olmayabilir. Varsa [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] yüklü, böyle bir program için EXE projesi oluşturabilirsiniz.  
  
### <a name="to-create-an-exe-project-for-an-existing-executable"></a>Varolan bir yürütülebilir dosya için bir EXE projesi oluşturmak için  
  
1.  Üzerinde **dosya** menüsünde tıklatın **açık** seçip **proje**.  
  
2.  İçinde **Proje Aç** iletişim kutusu, açılan listeyi tıklatın **dosya adı** kutusunda ve seçin **tüm proje dosyaları**.  
  
3.  Yürütülebilir dosyayı bulun ve tıklatın **Tamam**.  
  
     Bu yürütülebilir dosya içeren geçici bir çözüm oluşturur.  
  
### <a name="to-import-an-executable-into-a-visual-studio-solution"></a>Bir yürütülebilir dosya bir Visual Studio çözümüne aktarmak için  
  
1.  Üzerinde **dosya** menüsünde **Proje Ekle**ve ardından **mevcut proje**.  
  
2.  İçinde **Varolan Proje Ekle** iletişim kutusu, açılan listeyi tıklatın **dosya adı** kutusunda ve seçin **tüm proje dosyaları**.  
  
3.  Bulup yürütülebilir dosyayı seçin.  
  
4.  **Tamam**'ı tıklatın.  
  
5.  Yürütülebilir bir yürütme komutu seçerek Başlat **Başlat**, gelen **hata ayıklama** menüsü.  
  
    > [!NOTE]
    >  Programlama dillerinin tümü EXE projelerini desteklemez. Yükleme [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] bu özelliği kullanmak istiyorsanız.  
  
     Kaynak kodu olmayan yürütülebilir bir dosyada hata ayıklama, çalışan bir yürütülebilir ekleme ya da yürütülebilir dosyasına ekleyin kullanılabilir hata ayıklama özellikleri sınırlıdır bir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] çözüm. Yürütülebilir dosya uyumlu biçimde hata ayıklama bilgileri olmadan oluşturulduysa, kullanılabilir özellikler daha da sınırlı. Kaynak kodu varsa, kaynak koda içeri aktarmak için en iyi yaklaşım olan [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ve yürütülebilir dosya hata ayıklama yapısını oluşturmak [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata ayıklayıcı ayarları ve hazırlığı](../debugger/debugger-settings-and-preparation.md)   
 [Hata ayıklayıcısı güvenliği](../debugger/debugger-security.md)   
 [DBG dosyaları](http://msdn.microsoft.com/en-us/91e449e9-8b65-4123-960f-2107cd1f1cfd)



