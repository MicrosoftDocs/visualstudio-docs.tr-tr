---
title: Hizmet Başvurularında Sorun Giderme
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- msvse_wcf.Err.ReferenceGroup_NamespaceConflictsOther
- msvse_wcf.Err.AddSvcRefDlg_NothingSelectedOnGo
- msvse_wcf.Err.ErrorOnOK
- msvse_wcf.cfg.ConfigurationErrorsException
helpviewer_keywords:
- service references [Visual Studio], troubleshooting
- WCF services, troubleshooting
ms.assetid: 3b531120-1325-4734-90c6-6e6113bd12ac
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 471b62c35cbe7098d52e9cbeb08be29cd39c7d58
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2018
ms.locfileid: "39180431"
---
# <a name="troubleshoot-service-references"></a>Hizmet başvurularında sorun giderme

Bu konuda, Windows Communication Foundation (WCF) veya Visual Studio'da WCF Veri Hizmetleri başvuruları ile çalışırken oluşabilecek genel sorunları listelemektedir.

## <a name="error-returning-data-from-a-service"></a>Verileri hizmetten döndürülürken hata oluştu

Döndüğünüzde bir `DataSet` veya `DataTable` bir hizmetten bir "gelen iletiler için en büyük boyut kotası aşıldı" özel durumu alabilirsiniz. Varsayılan olarak, `MaxReceivedMessageSize` bazı bağlamalar özelliği, hizmet reddi saldırılarına maruz kalma riskinizi sınırlamak için görece küçük bir değere ayarlanır. Özel durum önlemek için bu değeri artırabilirsiniz. Daha fazla bilgi için bkz. <xref:System.ServiceModel.HttpBindingBase.MaxReceivedMessageSize%2A>.

Bu hatayı düzeltmek için:

1.  İçinde **Çözüm Gezgini**, çift *app.config* dosyasını açın.

2.  Bulun `MaxReceivedMessageSize` özellik ve daha büyük bir değere değiştirin.

## <a name="cannot-find-a-service-in-my-solution"></a>Bir hizmet çözümüm içinde bulunamıyor

Tıkladığınızda **bulma** düğmesine **hizmet başvuruları ekleme** iletişim kutusu, bir veya daha fazla WCF hizmet kitaplığı projeleri çözümdeki Hizmetler listesinde görünmez. Bu hizmet kitaplığı çözüme eklendi ancak henüz derlenmiş ortaya çıkabilir.

Bu hatayı düzeltmek için:

-   İçinde **Çözüm Gezgini**, WCF hizmet kitaplığı projesi sağ tıklatıp **yapı**.

## <a name="error-accessing-a-service-over-a-remote-desktop"></a>Bir hizmet Uzak Masaüstü erişilirken hata oluştu

Bir kullanıcı eriştiğinde bir Web barındırılan WCF hizmeti üzerinden bir Uzak Masaüstü Bağlantısı ve kullanıcı yönetici izinlerine sahip değil, NTLM kimlik doğrulaması kullanılır. Kullanıcı, kullanıcı yönetici izinlerine sahip değilse, aşağıdaki hata iletisini alabilirsiniz: "HTTP istek istemci kimlik doğrulama düzeni 'Anonymous' yetkilendirilmemiş. Sunucudan alınan kimlik doğrulama üst bilgisi 'NTLM' sağladı."

Bu hatayı düzeltmek için:

1.  Web sitesi projeyi **özellikleri** sayfaları.

2.  Üzerinde **Başlat seçenekleri** sekmesi, NET **NTLM kimlik doğrulaması** onay kutusu.

    > [!NOTE]
    > NTLM kimlik doğrulama özel olarak WCF hizmetlerini içeren Web siteleri için etkinleştirmeniz gerekir. WCF hizmetleri için güvenlik yapılandırmada aracılığıyla yönetilir *web.config* dosya. Bu, NTLM kimlik doğrulaması gereksiz kılar.

## <a name="access-level-for-generated-classes-setting-has-no-effect"></a>Erişim düzeyi ayarı sınıflar için hiçbir etkisi olmaz.

Ayarı **erişim sınıflar için erişim düzeyi** seçeneğini **yapılandırma hizmet başvuruları** iletişim kutusuna **dahili** veya **arkadaş** her zaman çalışmayabilir. İletişim kutusunda ayarlanacak seçenek görünür olsa da, sonuçta elde edilen destek sınıfları bir erişim düzeyi ile oluşturulan `Public`.

Bu bilinen gibi bu kullanılarak serileştirilmiş belirli bir türdeki sınırlamasıdır <xref:System.Xml.Serialization.XmlSerializer>.

## <a name="error-debugging-service-code"></a>Hata ayıklama hizmet kodu

İstemci kodundan bir WCF hizmeti için kodun içine adımladığınızda eksik sembollere ilgili bir hata alabilirsiniz. Çözümünüzün bir parçası olan bir hizmeti taşındığında veya çözümden kaldırıldı. Bu durum oluşabilir.

İlk geçerli çözümün bir parçası olan bir WCF hizmeti bir başvuru eklediğinizde, hizmet istemci projesi ve hizmet projesi arasında açık derleme bağımlılık eklenir. Bu, istemci her zaman güncel hizmet ikili dosyaları, istemci kodundan hizmet kodun içine Adımlama gibi senaryoları hata ayıklama için özellikle önemli olduğu erişimi olduğunu garanti eder.

Hizmet projeyi çözümden kaldırılırsa, bu açık derleme bağımlılık geçersiz kılınır. Visual Studio artık hizmet projesi yapılana gerektiğinde garanti edebilir.

Bu hatayı düzeltmek için hizmet projesi el ile yeniden oluşturmanız gerekir:

1.  Üzerinde **Araçları** menüsünü tıklatın **seçenekleri**.

2.  İçinde **seçenekleri** iletişim kutusunda **projeler ve çözümler**ve ardından **genel**.

3.  Emin olun **Show Gelişmiş derleme yapılandırmaları** onay kutusunun seçili olduğundan ve ardından **Tamam**.

4.  WCF hizmet projesini yükleyin.

5.  İçinde **Configuration Manager** iletişim kutusu, kümesi **etkin çözüm yapılandırması** için **hata ayıklama**. Daha fazla bilgi için [nasıl yapılır: yapılandırmaları oluşturma ve düzenleme](../ide/how-to-create-and-edit-configurations.md).

6.  İçinde **Çözüm Gezgini**, WCF Hizmeti projesini seçin.

7.  Üzerinde **derleme** menüsünde tıklatın **yeniden** WCF Hizmeti projeyi yeniden derlemek için.

## <a name="wcf-data-services-do-not-display-in-the-browser"></a>WCF Veri Hizmetleri tarayıcıda görüntüleme

Ne zaman çalışır bir XML temsilini verileri görüntülemek bir [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)], Internet Explorer verileri bir RSS akışı olarak hatalı yorumlayan. RSS akışlarını görüntüleme seçeneğinin devre dışı bırakıldığından emin olun.

Bu hatayı düzeltmek için RSS akışı devre dışı bırakın:

1.  Internet Explorer'da üzerinde **Araçları** menüsünde tıklatın **Internet Seçenekleri**.

2.  Üzerinde **içerik** sekmesinde **akışları** bölümünde **ayarları**.

3.  İçinde **akış ayarları** iletişim kutusu, NET **akış okuma görünümünde açmak** onay kutusunu işaretleyin ve ardından **Tamam**.

4.  Tıklayın **Tamam** kapatmak için **Internet Seçenekleri** iletişim kutusu.

## <a name="see-also"></a>Ayrıca bkz.

- [Windows Communication Foundation Hizmetleri ve Visual Studio'da WCF Veri Hizmetleri](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)