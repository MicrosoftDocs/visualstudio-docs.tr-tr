---
title: VBA oluşturmak veya Microsoft Office sistemi projesi için Visual Studio araçlarını açmak için erişimi etkinleştir
decsprition: You must explicitly enable access to the Office VBA project system before you can create or open a Visual Studio Tools for Office system project
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- vst.project.vbawrongversion
- VST.Project.VBASecurityGenericError
- VST.Project.VBASecurityPermissions
- VST.SelectDocWizard.MissingCOM
- VST.Project.VBASecurityNotSet
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f17c4e1481e7f33034e16d1e60a285b25c6f8230
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/22/2018
ms.locfileid: "34448997"
---
# <a name="enable-access-to-vba-to-create-or-open-a-visual-studio-tools-for-the-microsoft-office-system-project"></a>VBA oluşturmak veya Microsoft Office sistemi projesi için Visual Studio araçlarını açmak için erişimi etkinleştir

Oluşturmak veya Microsoft Office sistemi projesi için Visual Studio araçlarını açmak için Microsoft Office uygulamaları (VBA) proje sistemi için Visual Basic erişmeye açıkça etkinleştirmelisiniz.

 Microsoft Office geliştirme projelerini Visual Basic erişim uygulamalar için Visual Basic projeleri kullanmayın olsa bile Microsoft Office Word ve Microsoft Office Excel, Applications (VBA) proje sistem gerektirir. Tasarım zamanı desteği hem Visual Basic ve Visual C# projeleri denetimlerin uygulamaları proje sistemi için Visual Basic bağlıdır.

 Bazı Microsoft Office makrosu virüsler kendilerini yayılması için bir yol uygulamaları proje sistemi için Visual Basic otomatikleştirmek girişimi. Uygulamaları proje sistemi için Visual Basic Erişmeye etkinleştirerek makrosu virüs yayılmasını engellemeye yardımcı olan bir koruma'yı kaldırın. Ancak, makro güvenlik düzeyini ve Office uygulamalarınızı korumak Güvenilen Yayımcılar listesini herhangi makrosu bilgisayarınızda çalışıp çalışmayacağını belirleyecek şekilde normal makrosu güvenlik yerinde kalır.

> [!NOTE]
> Bu, yalnızca geliştirme bilgisayara uygulanır. Son kullanıcı bilgisayarları etkin Office çözümlerini çalıştırmak için bu seçenek gerekli değildir.

 Üzerinde uygulamaları proje sistemi için Visual Basic erişimi devre dışı bırakma kendi, virüslere karşı koruma sağlamaz, yalnızca bilgisayarınızı sürekli bir makro bulaşır ise diğer belgelere yayılmak gelen bazı virüsler durdurmaya yardımcı olduğunu dikkate almak önemlidir virüs. Bilgisayarınız için koruma eklendi katmanına olarak seçeneği varsayılan olarak devre dışıdır, ancak en iyi güvenlik uygulamalarını takip ediyorsanız etkinleştirmeden bilgisayarınızı daha açıktır. virüs yapmaz.

 En iyi koruma makrosu virüs olduğundan, yalnızca makrolarından güvenmek için yüksek veya çok yüksek güvenlik düzeyinde Office çalıştırmak için bilinen kaynakları doğrulandı Office karşı ve güvenlik yamaları ve virüs tarayıcılarını güncel kalmak için.

 Virüsler ve diğer kötü amaçlı kod bilgisayarınıza koruma hakkında daha fazla bilgi için bkz: [ http://www.microsoft.com/protect ](http://www.microsoft.com/protect).

 Etkinleştirmek veya devre dışı bırakma seçeneği **Visual Basic projesinde erişimi güven** el ile.

 VBA veya COM hata görürseniz Office yüklemenizin onarabilir.

## <a name="to-enable-or-disable-access-to-visual-basic-projects"></a>Etkinleştirmek veya Visual Basic projeleri erişimi devre dışı bırakmak için

1. Tıklatın **dosya** sekmesi.

2. Tıklatın **seçenekleri**.

3. Tıklatın **Güven Merkezi**ve ardından **Güven Merkezi Ayarları**.

4. İçinde **Güven Merkezi**, tıklatın **makrosu ayarları**.

5. İşaretleyin veya işaretini kaldırın **erişim VBA projesi nesne modeli güven** etkinleştirme veya Visual Basic projeleri erişimi devre dışı bırakma.

6. **Tamam**'ı tıklatın.

### <a name="to-enable-or-disable-access-to-visual-basic-projects-with-the-2007-microsoft-office-system"></a>Etkinleştirmek veya Visual Basic projeleri 2007 Microsoft Office sistemi ile erişimi devre dışı bırakmak için

1. Üzerinde **Araçları** menü Word veya Excel işaret **makrosu**ve ardından **güvenlik**.

2. İçinde **güvenlik** iletişim kutusu, tıklatın **Güvenilen Yayımcılar** sekmesi.

3. Etkinleştirmek için ya da temizleyin devre dışı bırakmak için seçin **Visual Basic projesinde erişimi güven**.

4. **Tamam**'ı tıklatın.

## <a name="to-set-your-office-macro-security-level"></a>Office makro güvenlik düzeyini ayarlamak için

1. Tıklatın **dosya** sekmesi.

2. Tıklatın **seçenekleri**.

3. Tıklatın **Güven Merkezi**ve ardından **Güven Merkezi Ayarları**.

4. İçinde **Güven Merkezi**, tıklatın **makrosu ayarları**.

5. İçinde **makrosu ayarları** bölümünde, istediğiniz ayarı seçin.

6. **Tamam**'ı tıklatın.

### <a name="to-set-your-office-macro-security-level-with-the-2007-microsoft-office-system"></a>2007 Microsoft Office sistemi ile Office makro güvenlik düzeyini ayarlamak için

1. Üzerinde **Araçları** menü Word veya Excel işaret **makrosu**ve ardından **güvenlik**.

2. Üzerinde **güvenlik düzeyini** sekmesinde, istediğiniz ayarı seçin.

    **Güvenlik düzeyini** sekmesi her düzeyi ayrıntılarını içerir. Daha fazla bilgi için Office Yardımı'nda "makro güvenlik düzeyleri" konusuna bakın.

### <a name="to-install-vba-with-the-2007-microsoft-office-system"></a>2007 Microsoft Office sistemi ile VBA yüklemek için

1. Denetim Masası'nda çalıştırmak **Program Ekle veya Kaldır** veya **programlar ve Özellikler**.

2. Office'te seçin **şu anda yüklü programlar** listesi.

3. **Değiştir**'i tıklatın.

4. Seçin **Özellikleri Ekle veya Kaldır**ve ardından **devam**.

5. Seçin **uygulamaların gelişmiş özelleştirmesini seç**ve ardından **sonraki**.

6. Genişletme **Office Paylaşılan Özellikler** içinde **uygulamalar ve araçlar için güncelleştirme seçeneklerini seçin** listesi.

7. Aşağı açılan menüyü açmak **Visual Basic for Applications**ve ardından **Bilgisayarım'dan Çalıştır**.

8. 
              **Devam**'a tıklayın.

9. **Kapat**'ı tıklatın.

## <a name="to-repair-your-installation-of-office"></a>Office yüklemesini onarmak için

1. Denetim Masası'nda çalıştırmak **Program Ekle veya Kaldır** veya **programlar ve Özellikler**.

2. Office sürümünüz seçin **şu anda yüklü programlar** listesi.

3. **Değiştir**'i tıklatın.

4. Seçin **yeniden yükle veya Onar**ve ardından **sonraki**.

5. Seçin **Office yükleme Algıla ve Onar hataları**ve ardından **yükleme**.

## <a name="see-also"></a>Ayrıca bkz.

 [Office çözümleri güvenli](../vsto/securing-office-solutions.md)