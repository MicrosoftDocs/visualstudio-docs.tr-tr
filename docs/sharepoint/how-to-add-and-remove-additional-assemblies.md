---
title: 'Nasıl yapılır: ek derlemeler ekleme ve kaldırma | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.RAD.CustomAssembly
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
ms.openlocfilehash: 4178f1ca5a437c52754199d26a6d39023193aaf8
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2018
ms.locfileid: "50219152"
---
# <a name="how-to-add-and-remove-additional-assemblies"></a>Nasıl yapılır: ek derlemeler ekleyip
  SharePoint paketinin, diğer derlemelerdeki işlevi veya verileri bağlıysa, derlemeleri, çözüm paketine (.wsp) ekleyebilirsiniz. Bu şekilde, SharePoint server özel derlemeler ile bir pakete yüklenmesini sağlar.  
  
 Ayrıca, ekleyin ve güvenli denetimler ve derlemeleri ile ilişkili sınıf kaynak dosyaları değiştirin.  
  
## <a name="add-additional-assemblies-safe-controls-and-class-resources"></a>Sınıf kaynakları ek bütünleştirilmiş kodları ve güvenli denetimler ekleme  
 SharePoint çözüm paketini Ek derlemelere ekleyebilirsiniz. Bir korumalı çözüm içindeki ek derlemeler genel derleme önbelleğine dağıtmak, ancak SharePoint Proje öğeleri bir korumalı çözüm içindeki içerik veritabanına eklenir. Bu ek derlemeler için güvenli denetimler ve sınıf kaynakları da ekleyebilirsiniz. Güvenli denetimler hakkında daha fazla bilgi için bkz: [sağlama paketleme ve dağıtım bilgileri proje öğelerinde](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) veya "Oluşturma bir SafeControl giriş materyali" olarak [dağıtma Web Bölümleri SharePoint Foundation'da](http://go.microsoft.com/fwlink/?LinkId=245505).  
  
#### <a name="to-add-an-existing-assembly"></a>Mevcut bir bütünleştirilmiş kodu eklemek için  
  
1.  Açık **paket Tasarımcısı**. Daha fazla bilgi için [nasıl yapılır: bir SharePoint çözüm paketini özelleştirme](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).  
  
2.  Seçin **Gelişmiş** sekmesi.  
  
3.  Seçin **Ekle** düğmesine ve ardından **mevcut bütünleştirilmiş kodu Ekle** listeden.  
  
     **Mevcut bütünleştirilmiş kodu Ekle** iletişim kutusu görüntülenir.  
  
4.  Üç noktayı seçin (![ASP.NET Mobil Tasarımcısı elips](../sharepoint/media/mwellipsis.gif "ASP.NET Mobil Tasarımcısı elips")), eklemek istediğiniz bütünleştirilmiş kod seçin. Seçilen derleme göreli yolu taşınabilirliği amacıyla kullanmanızı öneririz.  
  
5.  İçin **dağıtım hedefi**, seçin **GlobalAssemblyCache** derlemeyi genel bütünleştirilmiş kod önbelleğine dağıtın veya seçmek için seçenek düğmesini **WebApplication** seçeneği SharePoint çalıştıran sunucudaki WebApplication klasörüne derlemesini dağıtmak için düğmesi.  
  
#### <a name="to-add-an-assembly-from-project-output"></a>Proje çıkışından bütünleştirilmiş eklemek için  
  
1.  Açık **paket Tasarımcısı**.  
  
     Daha fazla bilgi için [nasıl yapılır: bir SharePoint çözüm paketini özelleştirme](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).  
  
2.  Seçin **Gelişmiş** sekmesi.  
  
3.  Seçin **Ekle** düğmesine ve ardından **proje çıkışından bütünleştirilmiş kodu Ekle** listeden.  
  
     **Proje çıkışından bütünleştirilmiş kodu Ekle** iletişim kutusu görüntülenir.  
  
4.  İçinde **kaynak proje** listelemek ve eklemek istediğiniz kaynak projesini seçin.  
  
5.  İçin **dağıtım hedefi**, seçin **GlobalAssemblyCache** derlemeyi genel bütünleştirilmiş kod önbelleğine dağıtın veya seçmek için seçenek düğmesini **WebApplication** seçeneği SharePoint çalıştıran sunucudaki WebApplication klasörüne derlemesini dağıtmak için düğmesi.  
  
#### <a name="to-add-a-safe-control"></a>Güvenli denetim eklemek için  
  
1.  Açık **mevcut bütünleştirilmiş kodu Düzenle** iletişim kutusu. Bunu yapmak için paket Tasarımcısı'nı açın, **Gelişmiş** sekmesinde, bir derleme seçin ve ardından **Düzenle** düğmesi.  
  
2.  İçinde **güvenli denetimler** bölmesinde seçin **yeni bir öğe eklemek için burayı tıklatın** düğmesi.  
  
3.  İçinde **derleme adı** sütun, derleme adını girin.  
  
4.  İçinde **Namespace** sütun, ad alanı için güvenli denetim adı girin.  
  
5.  İçinde **tür adı** sütun türü adını girin.  
  
#### <a name="to-add-a-class-resource"></a>Bir sınıf kaynak eklemek için  
  
1.  Açık **mevcut bütünleştirilmiş kodu Düzenle** iletişim kutusu. Bunu yapmak için paket Tasarımcısı'nı açın, **Gelişmiş** sekmesinde, bir derleme seçin ve ardından **Düzenle** düğmesi.  
  
2.  İçinde **sınıf kaynakları** bölmesinde seçin **yeni bir öğe eklemek için burayı tıklatın** düğmesi.  
  
3.  İçinde **dosya adı** sütun, üç noktayı seçin (![ASP.NET Mobil Tasarımcısı elips](../sharepoint/media/mwellipsis.gif "ASP.NET Mobil Tasarımcısı elips")) ve eklemek istediğiniz sınıf kaynağı seçin.  
  
## <a name="delete-custom-assemblies"></a>Derlemeleri Sil  
 Bir SharePoint paketi derlemeleri silmek ya da mevcut derlemelerden güvenli denetimler ve sınıf kaynakları silin.  
  
#### <a name="to-delete-an-existing-assembly"></a>Mevcut bir bütünleştirilmiş kodu silmek için  
  
1.  Açık **paket Tasarımcısı**. Daha fazla bilgi için [nasıl yapılır: bir SharePoint çözüm paketini özelleştirme](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).  
  
2.  Seçin **Gelişmiş** sekmesi.  
  
3.  İçinde **ek derlemeler** bölmesinde, silmek istediğiniz özel bütünleştirilmiş kod seçin.  
  
4.  Seçin **Sil** düğmesi.  
  
#### <a name="to-delete-a-safe-control-for-an-assembly"></a>Bir derleme için güvenli denetim silinemedi  
  
1.  Açık **mevcut bütünleştirilmiş kodu Düzenle** iletişim kutusu. Bunu yapmak için paket Tasarımcısı'nı açın, **Gelişmiş** sekmesinde, bir derleme seçin ve ardından **Düzenle** düğmesi.  
  
2.  Silmek istediğiniz güvenli denetim seçin.  
  
3.  Delete tuşunu seçin.  
  
#### <a name="to-delete-a-class-resource-for-an-assembly"></a>Bir derleme için bir sınıf kaynak silinemedi  
  
1.  Açık **mevcut bütünleştirilmiş kodu Düzenle** iletişim kutusu. Bunu yapmak için paket Tasarımcısı'nı açın, **Gelişmiş** sekmesinde, bir derleme seçin ve ardından **Düzenle** düğmesi.  
  
2.  Silmek istediğiniz sınıf kaynağı seçin.  
  
3.  Delete tuşunu seçin.  
  
## <a name="see-also"></a>Ayrıca bkz.
 [SharePoint özellikleri oluşturma](../sharepoint/creating-sharepoint-features.md)   
 [Nasıl yapılır: bir SharePoint özelliğini özelleştirme](../sharepoint/how-to-customize-a-sharepoint-feature.md)   
 [Nasıl yapılır: SharePoint özelliklerine öğe ekleyip](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)   
  
