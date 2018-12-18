---
title: 'Nasıl yapılır: uygulama ve dağıtım bildirimlerini imzalama'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- manifests [Visual Studio]
- code signing [Visual Studio], Authenticode
- deployment manifests [Visual Studio]
- signing manifests [Visual Studio]
- application manifests [Visual Studio]
- ClickOnce deployment [Visual Studio], signing assemblies
- key files [Visual Studio]
- assemblies [Visual Studio], signing
ms.assetid: 64173505-8bfb-41cf-a0de-b9075173f3a2
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 903bc0df9b24cd6f944e9e92c6dc5283cd1d25ea
ms.sourcegitcommit: 495bba1d8029646653f99ad20df2f80faad8d58b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/31/2018
ms.locfileid: "39381953"
---
# <a name="how-to-sign-application-and-deployment-manifests"></a>Nasıl yapılır: uygulama ve dağıtım bildirimlerini imzalama

Bir uygulamayı ClickOnce dağıtımını kullanarak yayınlamak istiyorsanız uygulama ve dağıtım bildirimlerinin ortak/özel anahtar çifti ile imzalanmış olması gerekir ve Authenticode teknolojisi kullanılarak. Windows sertifika deposu veya bir anahtar dosyasından bir sertifika kullanarak bildirimleri imzalayabilirsiniz.

 ClickOnce dağıtımı hakkında daha fazla bilgi için bkz. [ClickOnce güvenliği ve dağıtımı](../deployment/clickonce-security-and-deployment.md).

 ClickOnce bildirimlerini imzalanması için isteğe bağlı *.exe*-tabanlı uygulamaları. Daha fazla bilgi için bu belgedeki "imzalanmamış bildirimler oluşturmak" bölümüne bakın.

 Anahtar dosyaları oluşturma hakkında daha fazla bilgi için bkz: [nasıl yapılır: genel-özel anahtar çifti oluşturma](/dotnet/framework/app-domains/how-to-create-a-public-private-key-pair).

> [!NOTE]
> [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sahip yalnızca kişisel bilgi değişimi (PFX) anahtar dosyalarını destekler *.pfx* uzantısı. Ancak, farklı türde Sertifikalar Geçerli kullanıcının Windows sertifika deposundan tıklayarak seçebileceğiniz **Store ' seçin** üzerinde **imzalama** proje özellikleri.

## <a name="to-sign-application-and-deployment-manifests-using-a-certificate"></a>Uygulama ve dağıtım bildirimlerini imzalamak için bir sertifika kullanıyor

1.  Proje Özellikleri penceresine gidin ('nde proje düğümüne sağ **Çözüm Gezgini** seçip **özellikleri**, veya tür **proje özellikleri** içinde**Hızlı başlatma** penceresi veya tuşuna **Alt**+**Enter** içinde **Çözüm Gezgini**). Üzerinde **imzalama** sekmesinde **ClickOnce bildirimlerini imzala** onay kutusu.

2.  Tıklayın **Store ' seçin** düğmesi.

     **Bir sertifika seçin** iletişim kutusu görünür ve Windows sertifika deposunun içeriğini görüntüler.

    > [!TIP]
    > Tıklarsanız **sertifika özelliklerini görüntülemek için burayı tıklatın**, **sertifika ayrıntıları** iletişim kutusu görüntülenir. Bu iletişim kutusu sertifika ile ilgili ayrıntılı bilgiler içerir ve ek seçenekler içerir. Tıklayabilirsiniz **sertifikaları** görünümüne Ek Yardım bilgileri.

3.  Bildirimleri imzalamak için kullanmak istediğiniz sertifikayı seçin.

4.  Ayrıca, bir zaman damgası sunucusunun adresini belirleyebilirsiniz **zaman damgası sunucu URL'si** metin kutusu. Bu, bildirimin imzalandığı zamanı belirten bir zaman damgası sağlayan bir sunucudur.

## <a name="to-sign-application-and-deployment-manifests-using-an-existing-key-file"></a>Uygulama ve dağıtım bildirimlerini imzalamak için mevcut bir anahtar dosyasını kullanarak

1.  Üzerinde **imzalama** sayfasında **ClickOnce bildirimlerini imzala** onay kutusu.

2.  Tıklayın **dosyadan Seç** düğmesi.

     **Dosya Seç** iletişim kutusu görüntülenir.

3.  İçinde **Dosya Seç** iletişim kutusu, genel anahtar dosyasının konumuna göz atın (*.pfx*) kullanın ve ardından istediğiniz **açık**.

    > [!NOTE]
    > Bu seçenek olan dosyaları destekler *.pfx* uzantısı. Bir anahtar dosyası veya başka bir biçim, Windows sertifika deposuna kaydedin ve sertifikayı seçin sertifika varsa önceki yordamda açıklanmıştır. Seçilen sertifikanın amacı kod imzalamayı içermelidir.

     **Dosyasını açmak için parola gir** iletişim kutusu görüntülenir. (Varsa *.pfx* dosyası zaten Windows sertifika deponuza depolanır veya değil parola korumalı, size bir parola girmeniz istenmez.)

4.  Anahtar dosyaya erişmek için parolayı girin ve basın **Enter**.

## <a name="to-sign-application-and-deployment-manifests-using-a-test-certificate"></a>Uygulama ve dağıtım bildirimlerini imzalamak için bir test sertifikası kullanarak

1.  Üzerinde **imzalama** sayfasında **ClickOnce bildirimlerini imzala** onay kutusu.

2.  Test için yeni bir sertifika oluşturmak için tıklayın **Test sertifikası Oluştur** düğmesi.

3.  İçinde **Test sertifikası Oluştur** iletişim kutusunda, test sertifikanızın güvenliğinin sağlanmasına yardımcı olmak için bir parola girin.

## <a name="generate-unsigned-manifests"></a>İmzalanmamış bildirimler oluşturmak

ClickOnce bildirimlerini imzalanması için isteğe bağlı *.exe*-tabanlı uygulamaları. Aşağıdaki yordamlar imzasız ClickOnce bildirimlerinin nasıl oluşturulacağını gösterir.

> [!IMPORTANT]
> İmzalanmamış bildirimler, geliştirme ve test uygulamanızın basitleştirebilir. Ancak, imzalanmamış bildirimler üretim ortamında önemli güvenlik riskleri tanıtır. Yalnızca ClickOnce uygulamanız Internet veya diğer kötü amaçlı kod kaynaklarından tamamen yalıtılmış bir intranet bilgisayarda çalışıyorsa imzalanmamış bildirimleri kullanmayı düşünün.

 Varsayılan olarak, üretilen karmada bir veya daha fazla dosya özellikle hariç tutulmadığı sürece ClickOnce otomatik olarak imzalı bildirimler üretir. Diğer bir deyişle, tüm dosyalar karmaya uygulama sonuçları imzalı Bildirimlerde yayımlarken, bile **ClickOnce bildirimlerini imzala** onay kutusu işaretli değilse.

### <a name="to-generate-unsigned-manifests-and-include-all-files-in-the-generated-hash"></a>İmzalanmamış bildirimler oluşturmak ve tüm dosyaları oluşturulan karmaya dahil etmek için

1.  Tüm dosyalar karmaya dahil etmek imzalanmamış bildirimler oluşturmak için öncelikle uygulamayı imzalanmış bildirimlerle birlikte yayınlamanız gerekir. Bu nedenle, ilk önceki yordamlardan birini izleyerek ClickOnce bildirimlerini imzala ve ardından uygulamayı yayınlayın.

2.  Üzerinde **imzalama** sayfasında, NET **ClickOnce bildirimlerini imzala** onay kutusu.

3.  Yayınlama sürümünü, uygulamanızın yalnızca bir sürümü kalacak şekilde sıfırlayın. Varsayılan olarak, Visual Studio otomatik olarak uygulama yayımlama Yayımla sürümü her zaman değişiklik sayısını artırır. Daha fazla bilgi için [nasıl yapılır: ayarlama ClickOnce yayım sürümünü](../deployment/how-to-set-the-clickonce-publish-version.md).

4.  Uygulamayı yayınlayın.

### <a name="to-generate-unsigned-manifests-and-exclude-one-or-more-files-from-the-generated-hash"></a>İmzalanmamış bildirimler oluşturmak ve bir veya daha fazla dosya ve oluşturulan karmadan hariç tutmak için

1.  Üzerinde **imzalama** sayfasında, NET **ClickOnce bildirimlerini imzala** onay kutusu.

2.  Açık **uygulama dosyaları** iletişim kutusu ve kümesi **karma** için **hariç** ve oluşturulan karmadan hariç tutmak istediğiniz dosyaları için.

    > [!NOTE]
    > Bir dosyayı karma oluşturmadan hariç, böylece önceki yordamda gösterildiği imzalı bildirimleri önce yayınlamanız gerekmez bildirimler, otomatik imzalama devre dışı bırakmak üzere ClickOnce yapılandırır.

3.  Uygulamayı yayınlayın.

## <a name="see-also"></a>Ayrıca bkz.

- [Tanımlayıcı adlı derlemeler](/dotnet/framework/app-domains/strong-named-assemblies)
- [Nasıl yapılır: genel-özel anahtar çifti oluşturma](/dotnet/framework/app-domains/how-to-create-a-public-private-key-pair)
- [İmzalama sayfası, Proje Tasarımcısı](../ide/reference/signing-page-project-designer.md)
- [ClickOnce güvenliği ve dağıtımı](../deployment/clickonce-security-and-deployment.md)