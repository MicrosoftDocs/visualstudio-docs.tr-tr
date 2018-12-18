---
title: VC ++ proje ayarları, projeler ve çözümler, Seçenekler iletişim kutusu | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Projects.VCBuild
helpviewer_keywords:
- builds [Visual Studio], logs
- build process [C++]
- files [Visual Studio], built by C/C++ compiler
- file extensions, built by C or C++ compiler
- cl.exe compiler, file extensions
- extensions, files built by C or C++ compiler
- BuildLog.htm
ms.assetid: 56420efd-6a95-464e-b890-e2b38c48d66a
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a1491d639ace0cba80530ea1613525480bad07f5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49238868"
---
# <a name="vc-project-settings-projects-and-solutions-options-dialog-box"></a>VC++ Proje Ayarları, Projeler ve Çözümler, Seçenekler İletişim Kutusu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Bu iletişim kutusunu tanımlamanızı sağlar [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] proje dosya türlerini destekleyen ve günlük kaydı oluşturmak için ilgili ayarlar.  
  
### <a name="to-access-this-dialog-box"></a>Bu iletişim kutusuna erişmek için  
  
1.  Üzerinde **Araçları** menüsünü tıklatın **seçenekleri**.  
  
2.  Seçin **projeler ve çözümler**ve ardından **VC ++ proje ayarları**.  
  
## <a name="build-customization-search-path"></a>Derleme özelleştirme arama yolu  
 Yardımcı .rules dosyaları içeren dizinler listesini tanımlamak projeleriniz için derleme kuralları belirtir.  
  
## <a name="build-logging"></a>Günlük kaydı oluşturun  
 **Evet**  
 Derleme günlük dosyasının oluşturulmasını etkinleştirir. Bu seçeneği projenin Ara dosyaları dizininde bulunan BuildLog.htm üretir. Her yeni derleme önceki BuildLog.htm dosyanın üzerine yazar.  
  
 **Yok**  
 Derleme günlüğü dosyası oluşturulmasını devre dışı bırakır.  
  
## <a name="build-timing"></a>Zamanlama oluşturma  
 **Evet**  
 Derleme zamanlaması üzerinde kapatır. Seçili olduğunda, derleme tamamlamak geçen süre için çıkış penceresine gönderilir. Daha fazla bilgi için [çıkış penceresine](../../ide/reference/output-window.md).  
  
 **Yok**  
 Derleme zamanlaması devre dışı bırakır.  
  
## <a name="extensions-to-hide"></a>Gizlenecek uzantılar  
 İçinde görüntülenmeyecek dosyalarının dosya adı uzantılarını belirtir **Çözüm Gezgini** olduğunda **tüm dosyaları göster** etkinleştirilir.  
  
## <a name="extensions-to-include"></a>Dahil etmek için uzantıları  
 Projenize unity'nin dosyalarının dosya adı uzantılarını belirtir.  
  
## <a name="maximum-concurrent-c-compilations"></a>En fazla eşzamanlı C++ derlemesi  
 En fazla paralel C++ derlemesi için kullanılacak CPU çekirdeği sayısını belirtir.  
  
## <a name="show-environment-in-log"></a>Günlükte ortamı Göster  
 **Evet**  
 Derleme günlüğü dosyası ortam değişkenleri listeler. Bu seçenek, tüm ortam değişkenleri, oluşumunu sırasında yantısılmayacağını belirtir [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] projelere derleme günlüğü dosyası.  
  
 **Yok**  
 Ortam değişkenleri derleme günlük dosyasından hariç tutun.  
  
## <a name="solution-explorer-mode"></a>Çözüm Gezgini modu  
 **Projede sadece dosyaları göster**  
 Yapılandırır **Çözüm Gezgini** sadece projedeki dosyaları görüntülemek için.  
  
 **tüm dosyaları göster**  
 Yapılandırır **Çözüm Gezgini** diskteki proje klasöründeki dosya ve proje dosyaları göstermek için.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C/C++ programları oluşturma](http://msdn.microsoft.com/library/fa6ed4ff-334a-4d99-b5e2-a1f83d2b3008)   
 [C/C++ Derleme Başvurusu](http://msdn.microsoft.com/library/100b4ccf-572c-4d1f-970c-fa0bc0cc0d2d)



