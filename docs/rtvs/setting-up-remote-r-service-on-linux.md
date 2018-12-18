---
title: Linux üzerinde uzak R hizmeti ayarlama
description: Linux için Ubuntu ve Windows alt sistemi uzak R hizmeti ayarlama yapma.
ms.date: 12/04/2017
ms.prod: visual-studio-dev15
ms.technology: vs-rtvs
ms.topic: conceptual
author: kraigb
ms.author: kraigb
ms.reviewer: karthiknadig
manager: douge
ms.workload:
- data-science
ms.openlocfilehash: 81a0a5c26e91056e757bc6e6f68cd217e98c7e06
ms.sourcegitcommit: bccb05b5b4e435f3c1f7c36ba342e7d4031eb398
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/06/2018
ms.locfileid: "51220820"
---
# <a name="remote-r-service-for-linux"></a>Linux için Uzak R Hizmeti

Linux için Uzak R hizmeti şu anda rtvs daemon paketlenir. Arka plan programı desteklenen ve Linux için Ubuntu çalıştıran 16.10 LTS Masaüstü, sunucu ve Windows alt sistemi üzerinde Ubuntu 16.04 test. Bu makalede, toplu uzak R hizmeti bu farklı sistemlerinde ayarlanıyor ilişkin yönergeler sağlar.

Uzak makineye yapılandırdıktan sonra aşağıdaki adımları R araçları Visual Studio (RTVS için) bu hizmete bağlanabilir:

1. Seçin **R Araçları** > **Windows** > **çalışma alanları** açmak için **çalışma alanları** penceresi.
1. Seçin **Bağlantı Ekle**.
1. Bağlantı bir ad verin ve kendi URL'sini sağlayın `https://localhost:5444` (Linux için Windows alt) veya `https://public-ip:5444` (Azure container). Seçin **Kaydet** tamamlandığında.
1. Bağlantı simgesini seçin veya bağlantı öğeye çift tıklayın.
1. Oturum açma kimlik bilgilerini sağlayın. Kullanıcı adı ile önek eklenmelidir `<<unix>>\` olarak `<<unix>>\ruser1` (Uzak Linux bilgisayarlar için tüm bağlantılar için gerektiği gibi).
1. Otomatik olarak imzalanan sertifika kullanıyorsanız, bir uyarı görebilirsiniz. İleti uyarıyı düzeltmek için yönergeler sağlar.

## <a name="set-up-remote-r-service"></a>Uzak R hizmeti ayarlama

Bu bölümde, aşağıdaki seçenekleri açıklanmaktadır:

- [Ubuntu fiziksel bilgisayar](#physical-ubuntu-computer)
- [Ubuntu Server VM veya veri bilimi VM'si azure'da](#ubuntu-server-vm-or-data-science-vm-on-azure)
- [Yerel veya uzak Docker kapsayıcısı (temiz yapı)](#local-or-remote-docker-container-clean-build)
- [Azure Container Instances'ı üzerinde çalışan kapsayıcı](#container-running-on-azure-container-instances)

Her durumda, uzak bilgisayarda yüklü aşağıdaki R yorumlayıcı birine sahip olmalıdır:

- [Microsoft R Open](https://mran.microsoft.com/open/)
- [Windows için CRAN R](https://cran.r-project.org/bin/linux/ubuntu/)

### <a name="physical-ubuntu-computer"></a>Ubuntu fiziksel bilgisayar

1. Bilgisayarda oturum açtıktan sonra rtvs arka plan programı tarball indirin:

    ```bash
    wget -O rtvs-daemon.tar.gz https://aka.ms/r-remote-services-linux-binary-current
    tar -xvzf rtvs-daemon.tar.gz
    ```

1. Yükleme betiğini çalıştırın:

    ```bash
    sudo ./rtvs-install
    ```

    Sessiz bir Otomasyon için kullanmak `sudo ./rtvs-install -s`.

1. Etkinleştirin ve hizmeti başlatın:

    ```bash
    sudo systemctl enable rtvsd
    sudo systemctl start rtvsd
    ```

1. SSL sertifikası (üretim için gereklidir) yapılandırın. Varsayılan olarak, rtvs arka plan programı kullanır `ssl-cert-snakeoil.pem` ve `ssl-cert-snakeoil.pem` tarafından oluşturulan `ssl-cert` paket. Yükleme sırasında bunlar olarak bir araya `ssl-cert-snakeoil.pfx`. Üretim için yöneticiniz tarafından sağlanan SSL sertifikasını kullanın. SSL sertifikası sağlayarak yapılandırılabilir bir *.pfx* dosya ve isteğe bağlı içeri aktarma Parolada: */etc/rtvs/rtvsd.config.json*.

1. (İsteğe bağlı) Hizmetinin çalışıp çalışmadığını kontrol edin:

    ```bash
    ps -A -f | grep rtvsd
    ```

    Kullanıcı adı altında çalışan bir işlemin görmüyorsanız, `rtvssvc`. Başlatın aşağıdaki komutu kullanarak:

    ```bash
    sudo systemctl start rtvsd
    ```

1. Daha fazla rtvs daemon'ı yapılandırmak için bkz `man rtvsd`.

### <a name="ubuntu-server-vm-or-data-science-vm-on-azure"></a>Ubuntu Server VM veya veri bilimi VM'si azure'da

#### <a name="create-a-vm"></a>VM oluşturma

1. Oturum [Azure portalında](https://portal.azure.com).
1. Sanal makinelere gidin ve ardından **Ekle**.
1. Kullanılabilir VM görüntüleri listede, aramak ve aşağıdakilerden birini seçin:
    - Ubuntu sunucusu: `Ubuntu Server 16.04 LTS`
    - Veri bilimi sanal makinesi: `Linux Data Science` (bkz [veri bilimi sanal makineleri](https://azure.microsoft.com/services/virtual-machines/data-science-virtual-machines/) Ayrıntılar için)
1. Dağıtım modeli kümesine `Resource manager` seçip **Oluştur**.
1. VM için bir ad seçin, bir kullanıcı adı ve parola sağlayın (parola gereklidir, olarak SSH ortak anahtarı oturum açma desteklenmiyor).
1. VM yapılandırmasına istediğiniz diğer tüm değişiklikleri yapın.
1. VM boyutu seçme, yapılandırmasını doğrulayın ve seçin **Oluştur**. VM oluşturulduktan sonra sonraki bölüme geçin.

#### <a name="configure-the-vm"></a>VM yapılandırma

1. Sanal makinenin içinde **ağ** bölümünde, izin verilen gelen bağlantı noktası 5444 ekleyin. Farklı bir bağlantı noktası kullanmayı RTVS daemon yapılandırma dosyasında ayarını (*/etc/rtvs/rtvsd.config.json*).
1. (İsteğe bağlı) Bir DNS adı ayarlayın; IP adresini de kullanabilirsiniz.
1. WIndows için PuTTY gibi bir SSH istemcisi kullanarak VM'ye bağlanın.
1. Yönergelerini izleyin bir [fiziksel Ubuntu bilgisayar](#physical-ubuntu-computer) yukarıda.

### <a name="windows-subsystem-for-linux-wsl"></a>Linux (WSL) için Windows alt sistemi

1. Ya da WSL yükleme yönergelerini izleyin [Windows 10](/windows/wsl/install-win10#install-the-windows-subsystem-for-linux) veya [Windows Server](/windows/wsl/install-on-server#enable-the-windows-subsystem-for-linux-wsl).
1. Windows üzerinde bash'i başlatın ve önceki yönergeleri izleyerek bir [fiziksel Ubuntu bilgisayar](#physical-ubuntu-computer) bir özel durum. Adım 3 komutunu kullanarak hizmeti başlatın `rtvsd`yerine WSL systemd/systemctl arabirimleri şu anda desteklemediği için.

### <a name="local-or-remote-docker-container-clean-build"></a>Yerel veya uzak Docker kapsayıcısı (temiz yapı)

1. Uzak R hizmeti arka plan programı ve r en son sürümünü yükler aşağıdaki içeriğe sahip bir Docker dosyası oluşturma **Not**: Bu betik, parola olarak istediğiniz gibi değiştirebilirsiniz "foobar" ile "ruser1" adlı bir kullanıcı oluşturur. Son iki `RUN` deyimleri.

    ```docker
    FROM ubuntu:16.04

    ARG DEBIAN_FRONTEND=noninteractive

    RUN apt-get update \
     && apt-get install -y software-properties-common python-software-properties \
     && apt-get install -y apt-transport-https \
     && rm -rf /var/lib/apt/lists/*

    RUN sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ xenial main" > /etc/apt/sources.list.d/dotnetdev.list' \
     && apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 417A0893 \
     && sh -c 'echo "deb https://cran.revolutionanalytics.com/bin/linux/ubuntu xenial/" > /etc/apt/sources.list.d/cran-r.list' \
     && apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E084DAB9 \
     && rm -rf /var/lib/apt/lists/* \
     && apt-get clean

    RUN apt-get update --fix-missing && apt-get update \
     && apt-get install -y dotnet-dev-1.0.4 libexplain51 libzip4 libc6 git lshw ssl-cert wget \
     && rm -rf /var/lib/apt/lists/*

    # install R
    RUN apt-get update && apt-get install -y r-base-dev
    RUN apt upgrade -y

    # install rtvs-daemon
    RUN wget -O rtvs-daemon.tar.gz https://aka.ms/r-remote-services-linux-binary-current && tar -xvzf rtvs-daemon.tar.gz && ./rtvs-install -s

    RUN useradd --create-home ruser1
    RUN echo "ruser1:foobar" | chpasswd

    EXPOSE 5444
    ```

1. Derleme ve docker dosyasını çalıştırın:

    ```bash
    docker build -t myrimage .
    docker run -p 5444:5444 myrimage rtvsd
    ```

1. Bağlanmak için kullanım RTVS içeren `https://localhost:5444` yol, kullanıcı adı olarak `<<unix>>\ruser1`ve parola `foobar`. Kapsayıcı uzak bir bilgisayarda çalışıyorsa, kullanın `https://remote-host-name:5444` yol olarak bunun yerine. Bağlantı noktası güncelleştirerek değiştirilebilir */etc/rtvs/rtvsd.config.json*.

### <a name="container-running-on-azure-container-instances"></a>Azure Container Instances'ı üzerinde çalışan kapsayıcı

1. Bölümündeki yönergeleri [yerel veya uzak Docker kapsayıcısı (temiz yapı)](#local-or-remote-docker-container-clean-build) görüntüyü oluşturmak için.
1. Kapsayıcı, Docker hub veya Azure kapsayıcı deposuna gönderin.
1. Azure CLI'yı başlatın ve oturum `az login` komutu.
1. Kullanım `az container create` kapsayıcısı oluşturmak için komut kullanarak `--command-line "rtvsd"` çalıştırılacak kapsayıcısı ayarlamak ayarlamadıysanız `rtvsd` olarak bir `systemd` hizmeti. Aşağıdaki komutta, görüntüyü Docker hub üzerinde olması beklenir. Azure kapsayıcı deposuna kapsayıcı deposu kimlik bilgisi bağımsız değişkenleri komut satırına ekleyerek de kullanabilirsiniz.

    ```bash
    az container create --image myimage:latest --name myaz-container --resource-group myaz-container-res --ip-address public --port 5444 --cpu 2 --memory 4 --command-line "rtvsd"
    ```
1. Kullanım `az container list` durumunu denetlemek için komutu. Aranacak `provisioningState`: `Succeeded`.
1. Sağlama başarılı olursa, kapsayıcıya artık bağlanabilirsiniz. Genel IP adresi de arayın `ipAddress` docker dosyasının kimlik bilgileri ile kapsayıcıya RTVS bağlanmak için kullandığınız alanı.

