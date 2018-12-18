---
title: Belgelere güven verme
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], trust
- inclusion lists [Office development in Visual Studio], about inclusion lists
- trust [Office development in Visual Studio], 2007 Office system
- granting trust [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5dfa0ad9b27b94c472feabc0e202bd9eee58f08d
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50670916"
---
# <a name="grant-trust-to-documents"></a>Belgelere güven verme
  Belge düzeyi projesi aynı uygulama düzeyi projelere güvenlik gereksinimlerine sahiptir: bir sertifika ile bildirimleri imzalama veya güven istemi tıklayarak. Ayrıca, belge veya çalışma kitabı güvenli bir konuma atanan bir dizinde yer almalıdır.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="trusted-locations"></a>Güvenilen Konumlar  
 Uygulamalarda [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] ve Office 2010 güven merkezlerini burada kullanıcılar yapılandırabilir güvenilen konumları gibi güvenlik ve gizlilik ayarları. Office çözümleri için yerel bilgisayarın güvenilir olarak kabul edilir. Ancak, daha yüksek risk nedeniyle geçici bir klasör sistemin, her kullanıcı ve Internet Explorer gibi güvenilir olmayan belirli dizinleri vardır.  
  
 Güven Merkezi hakkında daha fazla bilgi için bkz. [güvenliğini ve ilkelerini ve ayarlarını Office 2010'daki](http://go.microsoft.com/fwlink/?LinkId=89202). Oluşturma, yönetme, kaldırmak ve güvenilen klasörlerini yapılandırma hakkında daha fazla bilgi için bkz. [2007 Office sisteminde Güvenilen Konumlar ve güvenilen yayımcılar ayarlarını yapılandırma](http://go.microsoft.com/fwlink/?LinkId=89203) ve [oluşturma, kaldırma veya değiştirme bir güvenilir, dosyaları için konum](https://support.office.com/article/Create-remove-or-change-a-trusted-location-for-your-files-f5151879-25ea-4998-80a5-4208b3540a62).  
  
## <a name="security-considerations-for-office-solutions"></a>Office çözümleriyle ilgili güvenlik konuları  
 Güvenilir konumlara eklemek için klasörleri düşünürken birçok güvenlik sorunları vardır:  
  
-   Yerel klasörler daha güvenli ve güvenilir örtük olarak kabul edilir. Dosya paylaşımları gibi uzak konumlardaki güvenilen konumları olarak işaretlenmesi gerekir.  
  
-   Bir dizin güvenilir konumlara eklediğinizde, bu eylem yalnızca Office çözümleri, aynı zamanda VBA ve ActiveX kod için tam güven verir. Bu nedenle, kök dizin ve *Belgelerim* klasörleri değil atanmış olarak güvenilir.  
  
-   Belgeyi güvenilir konumlara kullanarak güvenilen olsa da, ek izinler özelleştirme güvenmesi için gereklidir. Bir sertifika ile bildirimleri imzalama güven istemi tıklayarak ya da Office çözümü yükleme kullanarak özelleştirme için tam güven verebilirsiniz *Program dosyaları* dizin.  
  
-   Belge veya çalışma kitabı bir belge düzeyi çözümün derlemeyle aynı dizine veya farklı bir dizine depolayabilir. Örneğin, belgeyi bir SharePoint sunucusuna bulunamıyor ve bir ağ dosya paylaşımında derleme bulunamıyor. Daha fazla bilgi için [nasıl yapılır: bir belge düzeyinde Office çözümü ClickOnce kullanarak bir SharePoint sunucusuna yayımlama](https://msdn.microsoft.com/2408e809-fb78-42a1-9152-00afa1522e58).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Office çözümlerine güven verme](../vsto/granting-trust-to-office-solutions.md)   
 [Office çözüm güvenliğinde sorunlarını giderme](../vsto/troubleshooting-office-solution-security.md)   
 [Office çözümleri güvenliğini sağlama](../vsto/securing-office-solutions.md)  
  
  