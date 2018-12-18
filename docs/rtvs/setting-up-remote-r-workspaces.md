---
title: R için Uzak çalışma alanları
description: Nasıl uzak R çalışma alanlarını ayarlayın ve Visual Studio'dan bağlanabilir.
ms.date: 12/04/2017
ms.prod: visual-studio-dev15
ms.technology: vs-rtvs
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- data-science
ms.openlocfilehash: 207e4c2d6e7db9dd40288306b3a87086c4568f76
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49827720"
---
# <a name="set-up-remote-workspaces"></a>Uzak çalışma alanlarını ayarlayın

Bu makalede, uzak sunucu SSL ve uygun bir R hizmeti ile nasıl yapılandırılacağı açıklanmaktadır. Bu, R araçları için Visual Studio (sunucu üzerindeki uzak bir çalışma alanına bağlamak için RTVS) sağlar.

## <a name="remote-computer-requirements"></a>Uzak bilgisayar gereksinimleri

- Windows 10, Windows Server 2016 veya Windows Server 2012 R2. Ayrıca RTVS gerektirir
- [.NET framework 4.6.1](https://www.microsoft.com/download/details.aspx?id=49981) veya üzeri

## <a name="install-an-ssl-certificate"></a>Bir SSL sertifikası yükleme

Sunucuda bir SSL sertifikası gerektiren HTTP üzerinden bir uzak sunucu ile tüm iletişimler olur RTVS gerektirir. (Önerilen) bir güvenilen sertifika yetkilisi tarafından imzalanmış bir sertifika veya otomatik olarak imzalanan bir sertifika kullanabilirsiniz. (Otomatik olarak imzalanan bir sertifika bağlıyken sorunu uyarıları RTVS neden olur.) Tek ile ardından bilgisayara yükleyin ve özel anahtarıyla erişmesine izin vermek için ihtiyaç duyduğunuz.

### <a name="obtain-a-trusted-certificate"></a>Güvenilir bir sertifika alın

Güvenilen bir sertifika bir sertifika yetkilisi tarafından verilen (bkz [sertifika yetkilileri wikipedia](https://en.wikipedia.org/wiki/Certificate_authority) arka plan için). Gibi bir kamu kimlik kartı almak, güvenilen bir sertifika daha fazla işlem ve olası ücretleri içerir, ancak istek ve istek sahibi kimlik doğrulamasını yapar.

Sertifikada olması gereken anahtar alanı R server bilgisayarınıza tam etki alanı adıdır. Sertifika yetkilisi etki alanı için yeni bir sunucu oluşturmak için yetkiniz kavram gerektirir sunucunuza ait olduğu.

Daha fazla arka plan bilgileri için bkz [ortak anahtar sertifikaları](https://en.wikipedia.org/wiki/Public_key_certificate) wikipedia.

## <a name="install-an-ssl-certificate-on-windows"></a>Windows üzerinde bir SSL sertifikası yükleme

SSL sertifikası Windows üzerinde elle yüklenmesi gerekir. Bir SSL sertifikası yüklemek için aşağıdaki yönergeleri izleyin.

### <a name="obtain-a-self-signed-certificate-windows"></a>(Windows) otomatik olarak imzalanan sertifika edinme

Güvenilen bir sertifika varsa, bu bölümü atlayın. Güvenilir bir yetkili bir sertifika ile karşılaştırıldığında, otomatik olarak imzalanan bir sertifika bir kimlik kartı kendiniz oluşturmak kadar kolaydır. Bu işlem, Elbette, güvenilir bir yetkili ile çalışmayı daha çok daha kolay olsa da güçlü kimlik doğrulaması, bir saldırganın işaretsiz sertifika için kendi sertifika yerine ve istemci arasındaki trafiğin tümünün yakalama anlamına da azaltır ve Sunucu. Bu nedenle, *otomatik olarak imzalanan sertifika, yalnızca güvenilen bir ağda ve hiçbir zaman üretimde senaryolarını test etmek için kullanılmalıdır.*

Bu nedenle, RTVS her zaman otomatik olarak imzalanan bir sertifika ile sunucusuna bağlanırken aşağıdaki uyarıyı verir:

![Kendinden imzalı bir sertifika Uyarısı iletişim kutusu](media/workspaces-remote-self-signed-certificate-warning.png)

Otomatik olarak imzalanan bir sertifika vermek için:

1. Bir yönetici hesabını kullanarak R server bilgisayarda oturum açın.
1. Yeni bir yönetici PowerShell komut istemi açın ve aşağıdaki sorunu komutuyla değiştirerek `"remote-machine-name"` , server bilgisayarının tam etki alanı adı ile.

    ```ps
    New-SelfSignedCertificate -CertStoreLocation Cert:\LocalMachine\My -DnsName "remote-machine-name"
    ```

1. R sunucusu bilgisayarında hiç PowerShell önce çalıştırdıysanız, açıkça komutları çalıştırmayı etkinleştirmek üzere aşağıdaki komutu çalıştırın:

    ```ps
    Set-ExecutionPolicy -ExecutionPolicy RemoteSigned
    ```

Arka plan bilgileri için bkz. [otomatik olarak imzalanan sertifikalar](https://en.wikipedia.org/wiki/Self-signed_certificate) wikipedia.

### <a name="install-the-certificate"></a>Sertifika Yükleme

Uzak bilgisayarda bir sertifika yüklemek için çalıştırın *certlm.msc* (Sertifika Yöneticisi) bir komut isteminden. Sağ **kişisel** klasörü ve select **tüm görevler** > **alma** komutu:

![İçeri aktarma sertifika komutu](media/workspaces-remote-certificate-import.png)

### <a name="grant-permissions-to-read-the-ssl-certificates-private-key"></a>SSL sertifikasının özel anahtarının okuma izni verin

Sertifikayı içeri aktarıldıktan sonra vermek `NETWORK SERVICE` hesap özel anahtarı aşağıdaki yönergelerde açıklandığı okuma izni. `NETWORK_SERVICE` Hesap, sunucu bilgisayarına gelen SSL bağlantılarını sonlandıran bir hizmet olan R Hizmetleri Aracısı'nı çalıştırmak için kullanılır.

1. Çalıştırma *certlm.msc* (Sertifika Yöneticisi) bir yönetici komut isteminden.
1. Genişletin **kişisel** > **sertifikaları**sertifikanızı sağ tıklatın ve seçin **tüm görevler** > **özel yönetme Anahtarları**.
1. Sağ tıklatın ve sertifika **özel anahtarları Yönet** komutu altında **tüm görevler**.
1. Görüntülenen iletişim kutusunda, seçmek **Ekle** girin `NETWORK SERVICE` hesap adı:

    ![Özel anahtarlar iletişim kutusunda, network_servıce ekleme yönetme](media/workspaces-remote-manage-private-key-dialog.png)

1. Seçin **Tamam** iki kez iletişim kutularını kapatmak ve değişikliklerinizi işleyin.

## <a name="install-an-ssl-certificate-on-ubuntu"></a>Ubuntu üzerinde bir SSL sertifikası yükleme

`rtvs-daemon` Paket yükleme otomatik olarak imzalanan bir sertifika varsayılan olarak yüklemesinin bir parçası olarak.

### <a name="obtain-a-self-signed-certificate-ubuntu"></a>Otomatik olarak imzalanan bir sertifika (Ubuntu) alın

Avantajları ve riskleri otomatik olarak imzalanan sertifika kullanarak Windows açıklamasına bakın. `rtvs-daemon` Paket oluşturur ve yükleme sırasında otomatik olarak imzalanan sertifikayı yapılandırır. Otomatik olarak oluşturulan otomatik olarak imzalanan sertifikayı değiştirmek isterseniz bunu gerekecektir.

Kendiniz otomatik olarak imzalanan bir sertifika vermek için:

1. SSH veya Linux makinenizde oturum açın.
2. Yükleme `ssl-cert` paket:
    ```sh
    sudo apt-get install ssl-cert
    ```
3. Çalıştırma `make-ssl-cert` varsayılan otomatik olarak imzalanan SSL sertifikasını oluşturmak için:
    ```sh
    sudo make-ssl-cert generate-default-snakeoil --force-overwrite
    ```
4. PEM dosyaları ve oluşturulan anahtarı PFX dosyasına dönüştürün. Oluşturulan PFX giriş klasörünüzde olmalıdır:
    ```sh
    openssl pkcs12 -export -out ~/ssl-cert-snakeoil.pfx -inkey /etc/ssl/private/ssl-cert-snakeoil.key -in /etc/ssl/certs/ssl-cert-snakeoil.pem -password pass:SnakeOil
    ```

### <a name="configure-rtvs-daemon"></a>RTVS daemon'ı yapılandırma

SSL sertifika dosyası yolu (PFX yolu) ayarlanmalıdır */etc/rtvs/rtvsd.config.json*. Güncelleştirme `X509CertificateFile` ve `X509CertificatePassword` dosya yolunu ve parolası sırasıyla.

```json
{
  "logging": { "logFolder": "/tmp" },
  "security": {
    "allowedGroup": "",
    "X509CertificateFile": "/etc/rtvs/ssl-cert-snakeoil.pfx",
    "X509CertificatePassword": "SnakeOil"
  },
  "startup": { "name": "rtvsd" },
  "urls": "https://0.0.0.0:5444"
}
```

Dosyayı kaydedin ve daemon'u başlatmak `sudo systemctl restart rtvsd`.

## <a name="install-r-services-on-windows"></a>Windows üzerinde R services'ı yükleyin

R kodu çalıştırmak için Uzak bilgisayar gibi yüklü R yorumlayıcıya sahip olmanız gerekir:

1. İndirin ve aşağıdakilerden birini yükleyin:

   - [Microsoft R Open](https://mran.microsoft.com/open/)
   - [Windows için CRAN R](https://cran.r-project.org/bin/windows/base/)

     Her ikisi de aynı işlevselliğe sahiptir, ancak ek donanım Microsoft R Open avantajlar sağladığı için doğrusal Cebir kitaplıkları hızlandırılmış [Intel matematik çekirdek Kitaplığı](https://software.intel.com/intel-mkl).

2. Çalıştırma [R Hizmetleri yükleyicisi](https://aka.ms/rtvs-services) ve istendiğinde yeniden başlatın. Yükleyici şunları yapar:

    - Bir klasörde oluşturmak *%PROGRAMFILES%\R araçları Visual Studio\1.0\\*  ve gerekli tüm ikili dosyaları kopyalayın.
    - Yükleme `RHostBrokerService` ve `RUserProfileService` ve otomatik olarak başlayacak şekilde yapılandırın.
    - Yapılandırma `seclogon` hizmetini otomatik olarak başlayacak şekilde.
    - Ekleme *Microsoft.R.Host.exe* ve *Microsoft.R.Host.Broker.exe* gelen güvenlik duvarı kuralları 5444 varsayılan bağlantı noktası.

R services, bilgisayar yeniden başlatıldığında otomatik olarak Başlat:

- **R konak Aracısı hizmeti** R kodunu bilgisayar üzerinde çalıştığı işlem ile Visual Studio arasındaki tüm HTTPS trafiğini işler.
- **R kullanıcı profili hizmeti** Windows kullanıcı profili oluşturma işleyen ayrıcalıklı bir bileşendir. Yeni bir kullanıcı ilk R server bilgisayara oturum açtığında hizmeti olarak adlandırılır.

Bu hizmetler Hizmetleri yönetim konsolunda görebilirsiniz (*compmgmt.msc*).

## <a name="install-r-services-on-linux"></a>Linux'ta R Services'ı yükleme

R kodu çalıştırmak için Uzak bilgisayar gibi yüklü R yorumlayıcıya sahip olmanız gerekir:

1. İndirin ve aşağıdakilerden birini yükleyin:

   - [Microsoft R Open](https://mran.microsoft.com/open/)
   - [Windows için CRAN R](https://cran.r-project.org/bin/linux/ubuntu/)

     Her ikisi de aynı işlevselliğe sahiptir, ancak ek donanım Microsoft R Open avantajlar sağladığı için doğrusal Cebir kitaplıkları hızlandırılmış [Intel matematik çekirdek Kitaplığı](https://software.intel.com/intel-mkl).

2. Yönergeleri takip edin [Linux için Uzak R hizmeti](setting-up-remote-r-service-on-linux.md), fiziksel Ubuntu bilgisayarlar, Azure Ubuntu Vm'leri, Linux (WSL) ve Azure Container havuzda çalışan dahil olmak üzere, Docker kapsayıcıları için Windows alt sistemi kapsar.

## <a name="configure-r-services"></a>R services'ı yapılandırma

Uzak bilgisayarda çalışan R services ile Ayrıca kullanıcı hesaplarını oluşturmak için güvenlik duvarı kuralları ayarlamanıza, Azure ağı yapılandırma ve SSL sertifikası yapılandırma.

1. Kullanıcı hesapları: Uzak bilgisayar erişen her kullanıcı için hesapları oluşturun. Ya da standart (ayrılıklı olmayan) yerel kullanıcı hesaplarını oluşturabilir veya R server bilgisayarınızın etki alanınızla birleştirin ve uygun güvenlik gruplarına ekleme `Users` güvenlik grubu.

1. Güvenlik duvarı kuralları: varsayılan olarak, `R Host Broker` 5444 numaralı TCP bağlantı noktasını dinler. Bu nedenle, Windows Güvenlik duvarı kuralları için gelen ve giden trafiği etkin olduğundan emin olun (giden paketler ve benzer senaryoları yüklemek için gerekli değildir).  R Hizmetleri yükleyicisi bu kurallar yerleşik Windows Güvenlik Duvarı için otomatik olarak ayarlar. Bir üçüncü taraf güvenlik duvarı kullanıyorsanız, bağlantı noktası 5444 ancak açın `R Host Broker` el ile.

1. Azure yapılandırması: Uzak bilgisayardan Azure sanal makinede ise, bağlantı noktası 5444 gelen trafik için de, Windows Güvenlik duvarını bağımsız olarak Azure ağı içinde açın. Ayrıntılar için bkz [ağ güvenlik grubu ile ağ trafiğini filtreleme](https://docs.microsoft.com/azure/virtual-network/virtual-networks-nsg) Azure belgeleri.

1. R konak aracısı yüklemek için hangi SSL sertifikası bildirmek: sertifikanın bir Intranet sunucusunda yüklüyorsanız, sunucunuzun tam etki alanı adı, NetBIOS adıyla aynı olduğundan emin olma olasılığı yüksektir. Bu durumda, hiçbir şey yoktur yüklenen varsayılan sertifika olarak yapmak için gerekir.

    Ancak, sertifikanızın (örneğin, bir Azure VM) bir Internet'e yönelik sunucuya yüklüyorsanız, Internet'e yönelik sunucunun FQDN'sini hiçbir zaman NetBIOS adı ile aynı olduğu için sunucunuzun tam etki alanı adını (FQDN) kullanın.

    FQDN kullandığınız için R Services yüklendiği gidin (*% PROGRAM FILES%\R uzak hizmet için görsel Studio\1.0* varsayılan olarak), açık *Microsoft.R.Host.Broker.Config.json* dosyasını bir metin düzenleyicisinde ve içeriği ne olursa olsun, sunucunuzun FQDN, olduğu gibi kullanıcının için aşağıdaki, atama CN değiştirin `foo.westus.cloudapp.azure.com`:

    ```json
    {
      "server.urls": "https://0.0.0.0:5444",
      "security": {
        "X509CertificateName": "CN=your-server-fully-qualified-domain-name"
      }
    }
    ```

    Dosyayı kaydedin ve değişikliklerin uygulanması için bilgisayarı yeniden başlatın.

## <a name="troubleshooting"></a>Sorun giderme

**SORU. R server bilgisayarı yanıt vermiyor, ne yapmam gerekir?**

Komut satırından uzak bilgisayara ping atmayı deneyin: `ping remote-machine-name`. Ping başarısız olursa, bilgisayarı çalıştığından emin olun.

**SORU. R etkileşimli Penceresi'nde uzak bilgisayar, ancak neden hizmet çalışmıyor diyor?**

Üç olası nedeni vardır:

- [.NET framework 4.6.1](https://www.microsoft.com/download/details.aspx?id=49981) veya daha fazla bilgisayarda yüklü değil.
- Güvenlik duvarı kuralları için `Microsoft.R.Host.Broker` ve `Microsoft.R.Host` 5444 numaralı bağlantı noktasında gelen ve giden bağlantılar için etkin değil.
- Bir SSL sertifikası ile `CN=<remote-machine-name>` yüklü değil.

Yukarıdaki değişiklikleri yaptıktan sonra bilgisayarı yeniden başlatın. Ardından emin `RHostBrokerService` ve `RUserProfileService` ya da Görev Yöneticisi (Hizmetleri sekmesi) üzerinden çalışan veya *services.msc*.

**SORU. Neden R etkileşimli Penceresi'nde "401 Erişim reddedildi" R Server'a bağlanırken söylüyor?**

İki olası nedeni vardır:

- Büyük olasılıkla, `NETWORK SERVICE` hesabı, SSL sertifikasının özel anahtar erişimi yok. Vermek için önceki yönergeleri `NETWORK SERVICE` özel anahtara erişim.
- Emin olun `seclogon` hizmeti çalışıyor. Kullanım *services.msc* yapılandırmak için `seclogon` otomatik olarak başlatılacak.

**SORU. Neden R etkileşimli Penceresi'nde "404 bulunamadı" R Server'a bağlanırken söylüyor?**

Bu hata nedeniyle Visual C++ yeniden dağıtılabilir kitaplıklar eksik olabilir. R etkileşimli Penceresi'nde eksik kitaplığı (DLL) ilgili bir ileti olup olmadığını denetleyin. Ardından, VS 2015 yeniden dağıtılabilir'in yüklü olduğunu ve R de yüklü olduğunu denetleyin.

**SORU. R etkileşimli penceresinde internet/kaynak erişebilir olamaz, ne yapmalıyım?**

Emin olmak için güvenlik duvarı kuralları `Microsoft.R.Host.Broker` ve `Microsoft.R.Host` 5444 numaralı bağlantı noktasında giden erişime izin verin. Değişiklikler uygulandıktan sonra bilgisayarı yeniden başlatın.

**SORU. Bu çözümler denedim ve hala çalışmaz. Şimdi ne yapmalıyım?**

Günlük dosyalarına bakın *C:\Windows\ServiceProfiles\NetworkService\AppData\Local\Temp*. Bu klasör, çalıştırılan R Aracısı hizmetini her örneği için ayrı günlük dosyalarını içerir. Hizmet yeniden başlatıldığında yeni bir günlük dosyası oluşturulur. Yanlış neler hakkında ipuçları için en son günlük dosyasını denetleyin.
