---
title: 'Nasıl yapılır: gizli hata ayıklayıcı komutlarını geri yükleme | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, restoring commands
- debugging [Visual Studio], restoring commands
- commands, debugger
ms.assetid: 76ac9b77-f536-43b5-a9fc-984854b1c566
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b9ee37e72a52f866f5b67afaeacfd248628a3484
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2018
ms.locfileid: "39176849"
---
# <a name="how-to-restore-hidden-debugger-commands"></a>Nasıl Yapılır: Gizli Hata Ayıklayıcı Komutlarını Geri Yükleme
Visual Studio'yu kurarken IDE ayarları birincil programlama diliniz için bir dizi varsayılan seçmeniz istenir. Bazı diller için varsayılan IDE ayarları belirli hata ayıklayıcı komutları gizlemek.  
  
 Varsayılan IDE ayarlarınız tarafından gizlenen hata ayıklayıcı özelliği kullanmak istiyorsanız, komutu aşağıdaki yordamı kullanarak menüsüne geri ekleyebilirsiniz.  
  
### <a name="to-restore-hidden-debugger-commands"></a>Gizli hata ayıklayıcı komutlarını geri yükleme  
  
1.  Açık bir projeyle **Araçları** menüsünde tıklatın **Özelleştir**.  
  
2.  İçinde **Özelleştir** iletişim kutusu, tıklayın **komutları** sekmesi.  
  
3.  İçinde **menü çubuğu:** açılan listesinde, select **hata ayıklama** geri yüklenen komut içermesini istediğiniz menü.  
  
4.  Tıklayın **komut Ekle...**  düğmesi.  
  
5.  İçinde **Add Command** kutusunda, ardından istediğiniz komutu seçin **Tamam**.  
  
6.  Başka bir komut eklemek için önceki adımı yineleyin.  
  
7.  Tıklayın **Kapat** tamamladığınızda menüsüne komut ekleme.  
  
    > [!WARNING]
    >  Bazı menü öğeleri yalnızca hata ayıklayıcı çalışma modunda veya kesme moduna gibi belirli modda olduğunda görünür. Bu nedenle, bu adımları tamamladıktan sonra eklenen öğenin hemen görünür olmayabilir.  
  
## <a name="restoring-commands-not-available-from-the-customize-dialog-box"></a>Geri yükleme komutları kullanılamaz Özelleştir iletişim kutusu  
 Bazı komutlar, özellikle hiyerarşik menülerinde bulunan geri yüklenemez **Özelleştir** iletişim kutusu. Bu komutları geri yüklemek için IDE ayarları yeni bir koleksiyonu içeri aktarmanız gerekir.  
  
#### <a name="to-import-new-ide-settings"></a>Yeni IDE ayarları içeri aktarmak için  
  
1.  Üzerinde **Araçları** menüsünde tıklatın **içeri ve dışarı aktarma ayarları**.  
  
2.  Üzerinde **içeri aktarma ve dışarı aktarma ayarları Sihirbazı Hoş Geldiniz** sayfasında **seçili ortam ayarlarını içeri aktarma**ve ardından **sonraki**.  
  
3.  Üzerinde **geçerli ayarları Kaydet** sayfasında, mevcut ayarlarınızı kaydedin ve ardından gerekip gerekmediğini karar **sonraki**.  
  
4.  Üzerinde **içeri aktarmak için bir ayarlar koleksiyonu seçin** sayfasındaki **varsayılan ayarları** klasörü, kullanmak istediğiniz komutları olan geliştirme ayarlar koleksiyonu seçin. Hangi koleksiyonu seçmek için bilmiyorsanız deneyin **genel geliştirme ayarları** veya **Visual C++ geliştirme ayarları**, en iyi hata ayıklayıcı komutlarını sağlar.  
  
5.  **İleri**'ye tıklayın.  
  
6.  Üzerinde **ayarlarını içeri aktarmak için seçin** sayfasındaki **seçenekleri**, emin **hata ayıklama** seçilir. Bu ayarların yanı içe aktarmak istediğiniz sürece diğer onay kutularını temizleyin.  
  
7.  **Son**'a tıklayın.  
  
8.  Üzerinde **içeri aktarma tamamlandı** sayfasında, ayarlarınızı altında sıfırlama ile ilişkili hataları gözden geçirin **ayrıntıları**.  
  
9. **Kapat**'ı tıklatın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata ayıklayıcısı güvenliği](../debugger/debugger-security.md)   
 [Hata ayıklayıcı temel bilgileri](../debugger/getting-started-with-the-debugger.md)