---
title: Yardım Görüntüleyicisi Yönetici Kılavuzu
ms.date: 11/01/2017
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 4340c69f-b96b-4932-bb82-38b16a5ab149
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c58a0907f384c98ae3c1a341bc0e9be2794cdf18
ms.sourcegitcommit: 75e02ed88a1ace6e8265fd4e3a82a1bc78f3adca
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/13/2018
ms.locfileid: "53378187"
---
# <a name="help-viewer-administrator-guide"></a>Yardım Görüntüleyicisi Yönetici Kılavuzu

Yardım Görüntüleyici ile veya internet erişimi olmayan ağ ortamları için yerel Yardım yüklemelerini yönetmenize olanak sağlar. Yerel Yardım içeriği makine başına temelinde yapılandırılır. Varsayılan olarak, kullanıcılar, kendi yerel Yardım yüklemesini güncelleştirmek için yönetici haklarına sahip olmalıdır.

Ağ ortamınız istemcilerin Internet'e erişmesine izin veriyorsa kullanabilirsiniz **Yardım içeriği Yöneticisi** yerel Yardım içeriğini Internet üzerinden dağıtmak için çalıştırılabilir. Hakkında daha fazla bilgi için *HlpCtntMgr.exe* komut satırı sözdizimi, bkz: [için Yardım içeriği Yöneticisi komut satırı bağımsız değişkenleri](../help-viewer/command-line-arguments.md).

İçerik oluşturma hakkında daha fazla bilgi için bkz. bir intranet Hizmeti uç noktası ve benzeri etkinlik, türleri oluşturma [Yardım Görüntüleyicisi SDK](../extensibility/internals/microsoft-help-viewer-sdk.md).

Ağ ortamınızda internet erişimi yoksa, Yardım Görüntüleyici yerel Yardım içeriğini intranet ve bir ağ paylaşımına dağıtabilirsiniz. Kullanarak ayrıca Visual Studio IDE Yardım seçeneklerini devre dışı bırakabilirsiniz [kayıt defteri anahtarını geçersiz](../help-viewer/behavior-overrides.md) gibi işlevler için:

- çevrimiçi ve çevrimdışı Yardım

- IDE'nin IDE'nin ilk başlatılmasında içerik yükleme

- intranet içerik hizmeti belirtme

- İçeriği yönetme

## <a name="deploy-local-help-content-from-the-internet"></a>Yerel Yardım içeriğini Internet üzerinden dağıtma

Kullanabileceğiniz **Yardım içeriği Yöneticisi** (*HlpCtntMgr.exe*) yerel Yardım içeriğini Internet'ten istemci bilgisayarlara dağıtmak için. Aşağıdaki sözdizimini kullanın:

```cmd
\\%ProgramFiles(x86)%\Microsoft Help Viewer\v2.3\HlpCtntmgr.exe /operation \<*name*> /catalogname \<*catalog name*> /locale \<*locale*>
```

Hakkında daha fazla bilgi için *HlpCtntMgr.exe* komut satırı sözdizimi, bkz: [için Yardım içeriği Yöneticisi komut satırı bağımsız değişkenleri](../help-viewer/command-line-arguments.md).

Gereksinimler:

-   İstemci bilgisayarların Internet'e erişimi olmalıdır.

-   Kullanıcılar, güncelleştirme, ekleme veya yüklendikten sonra yerel Yardım içeriğini kaldırmak için yönetici haklarına sahip olmalıdır.

Uyarılar:

-   Yardım için varsayılan kaynak çevrimiçi olmaya devam edecektir.

### <a name="example"></a>Örnek

Aşağıdaki örnek, Visual Studio için İngilizce içeriği bir istemci bilgisayara yükler.

#### <a name="to-install-english-content-from-the-internet"></a>Internet'ten İngilizce içeriği yüklemek için

1.  Seçin **Başlat** seçip **çalıştırma**.

2.  Aşağıdakileri yazın:

     `C:\Program Files (x86)\Microsoft Help Viewer\v2.3\hlpctntmgr.exe /operation install /catalogname VisualStudio15 /locale en-us`

3.  Tuşuna **girin**.

## <a name="deploy-pre-installed-local-help-content-on-client-computers"></a>İstemci bilgisayarlarda önceden yüklenmiş yerel Yardım içeriğini dağıtma

İçerik kümesi Online'dan tek bir bilgisayara yükleyin ve ardından, yüklenen içerik kümesini başka bilgisayarlara kopyalayabilirsiniz.

Gereksinimler:

-   İçerik kümesini yüklediğiniz bilgisayarın internet erişimi olmalıdır.

-   Kullanıcılar, güncelleştirme, ekleme veya yüklendikten sonra yerel Yardım içeriğini kaldırmak için yönetici haklarına sahip olmalıdır.

    > [!TIP]
    > Kullanıcıların yönetici hakları yoksa, devre dışı bırakmayı önerilir **içeriği Yönet** Yardım Görüntüleyicisi'nde sekmesi. Daha fazla bilgi için [Yardım İçerik Yöneticisi geçersiz kılmaları](../help-viewer/behavior-overrides.md).

Uyarılar:

-   Yardım için varsayılan kaynak çevrimiçi olmaya devam edecektir.

### <a name="create-the-content-set"></a>İçerik kümesi oluşturma

Temel içerik kümesini oluşturabilmeniz için önce hedef bilgisayardaki tüm yerel Visual Studio içeriğini kaldırmanız gerekir.

#### <a name="to-uninstall-local-help"></a>Yerel Yardımı kaldırmak için

1. Yardım Görüntüleyici'de seçin **içeriği Yönet** sekmesi.

2. Visual Studio belge kümesine gidin.

3. Seçin **Kaldır** her bir alt öğenin yanında.

4. Seçin **güncelleştirme** kaldırmak için.

5. Gözat *%ProgramData%\Microsoft\HelpLibrary2\Catalogs\VisualStudio15* ve klasörün yalnızca dosya içerdiğini doğrulayın *catalogType.xml*.

   Tüm önceden yüklenmiş yerel Visual Studio Yardım içeriğini kaldırdıktan sonra temel içerik kümesini yüklemeye hazırsınız demektir.

#### <a name="to-download-the-content"></a>İçerik indirmek için

1.  Yardım Görüntüleyici'de seçin **içeriği Yönet** sekmesi.

2.  Altında **önerilen belgeleri** veya **kullanılabilir belgeler**, indirin ve ardından istediğiniz belge kümelerine gidin **Ekle**.

3.  Seçin **güncelleştirme**.

Ardından, istemci bilgisayarlara dağıtılacak şekilde içeriği paketlemek gerekir.

#### <a name="to-package-the-content"></a>İçeriği paketlemek için

1.  Daha sonra dağıtım için içeriğin kopyalanacağı bir klasör oluşturun. Örneğin: *C:\VSHelp*.

2.  Açık *cmd.exe* yönetici izinlerine sahip.

3.  1. adımda oluşturduğunuz klasöre gidin.

4.  Aşağıdakileri yazın:

     `Xcopy %ProgramData%\Microsoft\HelpLibrary2 \<*foldername*>\ /y /e /k /o `

     Örneğin: `Xcopy %ProgramData%\Microsoft\HelpLibrary2 c:\VSHelp\ /y /e /k /o`.

### <a name="deploy-the-content"></a>İçerik dağıtma

1.  Bir ağ paylaşımı oluşturmanız ve Yardım içeriğini bu konuma kopyalayın.

     Örneğin, içeriği kopyalayın *C:\VSHelp* için  *\\\myserver\VSHelp*.

2.  Oluşturma bir *.bat* Yardım içeriği için dağıtım betiği içeren dosya. İstemci büyük olasılıkla bir okuma kilidi itmenin parçası silinen dosyaların hiçbirinde olabileceğinden, güncelleştirmeleri göndermeden önce kapatma istemci olmalıdır. Örneğin:

    ```cmd
    REM - copy pre-ripped content to ProgramData
    Xcopy %~dp0HelpLibrary2 %SYSTEMDRIVE%\ProgramData\Microsoft\HelpLibrary2\ /y /e /k /o
    if ERRORLEVEL 1 ECHO *** ERROR COPYING Help Library files to ProgramData (%ERRORLEVEL%)
    ```

3.  Çalıştırma *.bat* Yardım içeriğini yüklemek istediğiniz makinelerde yerel dosya.

## <a name="see-also"></a>Ayrıca bkz.

- [Komut satırı bağımsız değişkenleri için Yardım içeriği Yöneticisi](../help-viewer/command-line-arguments.md)
- [Yardım İçerik Yöneticisi geçersiz kılmaları](../help-viewer/behavior-overrides.md)
- [Microsoft Yardım Görüntüleyicisi](../help-viewer/overview.md)
- [Yardım Görüntüleyicisi SDK'sı](../extensibility/internals/microsoft-help-viewer-sdk.md)