---
title: Office çözümleri genel bakış yerel veritabanı dosyaları kullanma
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], data
- data [Office development in Visual Studio], local
- local data [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 01e9dc3df93e1f721eba9ce3bcf65d4fb8bb1ca1
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/05/2018
ms.locfileid: "34767588"
---
# <a name="use-local-database-files-in-office-solutions-overview"></a>Office çözümleri genel bakış yerel veritabanı dosyaları kullanma
  SQL Server Express gibi bir veritabanı dosyası içerebilir (*.mdf*) dosyası ya da Microsoft Office Access (*.mdb*) dosyasında Office çözümü. Bu, son kullanıcıların merkezi veritabanı bakımının örneğin yalnızca tek bir bilgisayarda kullanılan bir yerel stok çözümüne gerekli olduğu durumlarda yerel bir veritabanı bulundurmanız sağlar.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="import-the-database-file-into-a-project"></a>Veritabanı dosyası projeye alma  
 Veritabanı dosyasını projenize içeri aktarmak için kullanın **veri kaynağı Yapılandırma Sihirbazı** veritabanı dosyasına dayalı bir veri kaynağı oluşturmak için. Sihirbaz, veritabanı dosyası ve bir türü belirtilmiş veri kümesi projenize ekler.  
  
## <a name="deploy-the-database-file"></a>Veritabanı dosyasını dağıtma  
 **Veri kaynağı Yapılandırma Sihirbazı** yerel veritabanı dosyasına bağlantılar oluşturmak için göreli bir yol kullanır. Bu, dosyaların göreli konumları sahipseniz çözümü bir bilgisayardan diğerine kopyalamak sağlar.  
  
 Bir sunucuya çözümünüzü dağıtmak ve sonra belgeyi her son kullanıcıya dağıtın, gerekir el ile de veritabanı dosyasını dağıtın ve aynı konumda yer alan belge göre yükleyin. Çözemiyorsa veritabanı dosyasını da taşır sürece bu, son kullanıcı kendi bilgisayarda yeni bir konuma belge taşıyamazsınız anlamına gelir.  
  
## <a name="local-database-files-and-caching-the-dataset"></a>Yerel veritabanı dosyaları ve veri kümesi önbelleğe alma  
 Microsoft Office Excel ve Microsoft Office Word için belge düzeyi çözümlerde, belge kümelerinde öznitelik dataset örneğiyle işaretleyerek önbelleğe alabilirsiniz <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>. Eklediğinizde veritabanı dosyasını projenize kullanarak **veri kaynağı Yapılandırma Sihirbazı**, türü belirtilmiş veri kümesi projenize otomatik olarak eklenir. Uygulanacak nadiren gereklidir <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> bu veri kümesine veri zaten kullanıcının bilgisayarında yerel olduğundan. Daha fazla bilgi için bkz: [veriyi önbelleğe](../vsto/caching-data.md).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Office çözümlerinde denetimlere veri bağlama](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Nasıl yapılır: belgeleri veritabanı verileriyle doldurma](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [Nasıl yapılır: konak kontrolü verileriyle veri kaynağını güncelleme](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md)   
 [Verileri önbelleğe](../vsto/caching-data.md)  
  
  