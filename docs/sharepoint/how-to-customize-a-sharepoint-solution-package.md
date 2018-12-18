---
title: 'Nasıl yapılır: bir SharePoint çözüm paketini özelleştirme | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.RAD.PackageDesignerAdvanced
- VS.SharePointTools.RAD.PackageDesigner.Manifest
- VS.SharePointTools.RAD.PackageDesignerProperties
- VS.SharePointTools.RAD.PackageDesigner.SwitchView
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: fd1ebe9e49a0b3e26d090fdbbdbbe4dd37c0344a
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37120600"
---
# <a name="how-to-customize-a-sharepoint-solution-package"></a>Nasıl yapılır: bir SharePoint çözüm paketini özelleştirme
  Paket tasarımcısını oluşturmak ve bir paket özelleştirmek için kullanabileceğiniz (*.wsp*). Örneğin, SharePoint Proje öğeleri ve Özellikler ekleme, Web sunucusu çözümü dağıtıldığında sıfırlamak ve dağıtım sunucusu türü ayarlayın, belirtin.  
  
## <a name="open-the-package-designer"></a>Paket tasarımcısını açın  
  
#### <a name="to-open-the-package-designer"></a>Paket Tasarımcısı'nı açmak için
  
-   İçinde **Çözüm Gezgini**, çift **paket**, veya seçin **Görünüm Tasarımcısı** için kısayol menüsünde **paket**.  
  
## <a name="view-the-packaged-manifestffile"></a>Paketlenmiş manifestfFile görüntüleyin  
 Paket bildirim dosyası oluşturmak ve değiştirmek için paket tasarımcısını kullanabilirsiniz. Ardından, Visual Studio'da bu dosya için XML kodunu görüntüleyebilirsiniz.  
  
#### <a name="to-view-the-xml-source-file"></a>XML kaynak dosyası görüntülemek için  
  
1.  İçinde **paket tasarımcısını**, seçin **bildirim**.  
  
#### <a name="to-view-the-packaged-manifest-file-by-using-solution-explorer"></a>Çözüm Gezgini kullanarak paket bildirim dosyasının görüntülemek için  
  
1.  İçinde **Çözüm Gezgini**, seçin **tüm dosyaları göster**.  
  
2.  Paket genişletin, Package.package genişletin ve ardından açın *Package.Template.xml* dosya.  
  
    > [!NOTE]  
    >  Paketi şablonu için bildirim XML dosyası açtığınızda, dosyaları otomatik olarak doğrulanır ve Hata Listesi penceresinde görünen uyarıları göz ardı edebilirsiniz.  
  
## <a name="change-the-manifest-template"></a>Bildirim şablonunu değiştirme  
 Visual Studio XML Düzenleyicisi'ni veya şablon bildirim bölmesini paket bildirim dosyasında için XML kodunu değiştirebilirsiniz. XML kodunu değişiklikler paketi için paket bildirim dosyasının birleştirilir.  
  
#### <a name="to-change-the-manifest-template-by-using-the-xml-editor"></a>XML Düzenleyicisi'ni kullanarak bildirim şablonu değiştirmek için  
  
1.  İçinde **paket tasarımcısını**, seçin **bildirim** sekmesinde, genişletin **seçeneklerini Düzenle** düğümünü ve ardından **XML düzenleyicisinde açın** bağlantı.  
  
     XML değişiklikler paket bildirim dosyasının birleştirilir.  
  
#### <a name="to-change-the-manifest-template-by-using-the-manifest-template-pane"></a>Bildirim şablonu bölmesini kullanarak bildirim şablonu değiştirmek için  
  
1.  İçinde **paket tasarımcısını**, seçin **bildirim** sekmesinde, genişletin **seçeneklerini Düzenle** düğümü ve bildirim şablonu bölmesinde görüntülenen XML değiştirin.  
  
     XML değişiklikler görünür **paketlenmiş, Önizleme bildirim** bölmesi.  
  
## <a name="overwrite-the-packaged-manifest-file"></a>Paket bildirim dosyasının üzerine yaz  
 Paket tasarımcısını devre dışı bırakabilir ve oluşturma *manifest.xml* el ile dosya. Bu yordamı gerçekleştirmek ilk kez paket tasarımcısını geçerli ayarlarında paketi şablonu XML dosyasına kaydedilir. Ardından, değiştirmek veya XML kodunu üzerine yazabilirsiniz.  
  
> [!NOTE]  
>  Bu proje öğeleri ve Özellikler ekleme veya paket tasarımcısını devre dışı durumdayken SharePoint Proje öğeleri ve Özellikler XML dosyasında kaldırırsanız, paket değil.  
  
#### <a name="to-overwrite-packaged-manifest-file-by-disabling-the-designer"></a>Tasarımcı devre dışı bırakarak paket bildirim dosyasının üzerine yazmak için  
  
1.  İçinde **paket tasarımcısını**, seçin **bildirim** sekmesi.  
  
2.  Genişletin **seçeneklerini Düzenle** düğümü seçin **üzerine yaz oluşturulan XML ve düzenleme bildiriminde XML Düzenleyicisi'ni** bağlamak ve ardından **Evet** düğmesi.  
  
     Şablonu geçerli paket bildirim dosyası güncelleştirilir.  
  
## <a name="enable-the-package-designer"></a>Paket tasarımcısını etkinleştir  
 Özelleştirmek için paket tasarımcısını yeniden etkinleştirebilirsiniz *manifest.xml* dosya.  
  
#### <a name="to-re-enable-the-designer"></a>Tasarımcı yeniden etkinleştirmek için  
  
1.  İçinde **paket tasarımcısını**, seçin **atma bildirim düzenleme ve yeniden Tasarımcısı'nı etkinleştirmeniz** bağlamak ve ardından **Evet** düğmesi.  
  
     Şablon özgün metinle yenilenir ve XML değişiklikler kaybolur.  
  
## <a name="see-also"></a>Ayrıca bkz.
 [Paket ve SharePoint çözümlerini dağıtma](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
