---
title: Visual Studio derleme araçları bir kapsayıcıya yükleme
titleSuffix: ''
description: Visual Studio derleme araçları, sürekli tümleştirme ve sürekli teslim (CI/CD) iş akışlarını destekleyen bir Windows kapsayıcısına yüklemeyi öğrenin.
ms.date: 04/18/2018
ms.technology: vs-acquisition
ms.custom: seodec18
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: d5c038e2-e70d-411e-950c-8a54917b578a
author: heaths
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cdb7148560dfca966b82d8d9cef617075752a58b
ms.sourcegitcommit: 8cdc6e2ad2341f34bd6b02859a7c975daa0c9320
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/12/2018
ms.locfileid: "53307719"
---
# <a name="install-build-tools-into-a-container"></a>Derleme araçları bir kapsayıcıya yükleme

Visual Studio derleme araçları, sürekli tümleştirme ve sürekli teslim (CI/CD) iş akışlarını destekleyen bir Windows kapsayıcısına yükleyebilirsiniz. Bu makalede hangi Docker yapılandırma değişikliklerini ne yanı sıra gerekli aracılığıyla kılavuzları [iş yüklerinin ve bileşenlerin](workload-component-id-vs-build-tools.md) bir kapsayıcıda yükleyebilirsiniz.

[Kapsayıcıları](https://www.docker.com/what-container) yalnızca bir CI/CD sunucu ortamında, ancak geliştirme ortamları için kullanabileceğiniz bir tutarlı yapı sistemi paketlemek için harika bir yoludur. Örneğin, kaynak kodunuzu kodunuzu yazmak için Visual Studio veya diğer araçları kullanmaya devam ederken, özelleştirilmiş bir ortamı tarafından oluşturulacak bir kapsayıcıya bağlayabilir. CI/CD akışınızı aynı kapsayıcı görüntüsü kullanıyorsa, tutarlı bir şekilde, kodunuzun derlendiğinden güvenli yaslayabilirsiniz. Kapsayıcıları, birden çok kapsayıcı bir düzenleme sistemi ile kullanarak mikro hizmetler için ortak olan çalışma zamanı tutarlılık için de kullanabilirsiniz; Ancak, bu makalenin kapsamı dışındadır olur.

Visual Studio derleme araçları, kaynak kodunuzu derlemek için ihtiyacınız yoksa, aynı adımları diğer Visual Studio ürünleri için kullanılabilir. Ancak, komutların otomatik şekilde Windows kapsayıcıları etkileşimli bir kullanıcı arabirimi desteklemediğini unutmayın.

## <a name="overview"></a>Genel Bakış

Kullanarak [Docker](https://www.docker.com/what-docker) kaynak kodunuzu derleme kapsayıcılar, oluşturabileceğiniz bir görüntü oluşturun. Örneğin, en son Visual Studio derleme araçları 2017 ve kaynak kodu oluşturmak için sıklıkla kullanılan diğer bazı yardımcı programlar Dockerfile yükler. Daha fazla diğer araçlar ve testleri çalıştırmak için yapı çıktı yayımlama komut dosyalarını dahil etmek için kendi Dockerfile ve daha fazlasını da değiştirebilirsiniz.

Docker için Windows daha önce yüklediyseniz, 3. adımına atlayabilirsiniz.

## <a name="step-1-enable-hyper-v"></a>Adım 1. Hyper-V olanağını etkinleştir

Hyper-V varsayılan olarak etkin değildir. Docker için Windows başlatmak için etkinleştirilmelidir; yalnızca Hyper-V yalıtım Windows 10 için bu yana şu anda desteklenmiyor.

* [Windows 10 Hyper-V etkinleştir](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v)
* [Windows Server 2016 Hyper-V etkinleştir](https://docs.microsoft.com/windows-server/virtualization/hyper-v/get-started/install-the-hyper-v-role-on-windows-server)

> [!NOTE]
> Makinenizde sanallaştırma etkinleştirilmelidir. Bu, genellikle varsayılan olarak etkindir; Ancak, Hyper-V yükleme başarısız olursa, sanallaştırma etkinleştirme için sistemi belgelerinize bakın.

## <a name="step-2-install-docker-for-windows"></a>Adım 2. Windows için Docker'ı yükleyin

Windows 10 kullanıyorsanız, yapabilecekleriniz [Docker Community Edition'ı yükleyip](https://docs.docker.com/docker-for-windows/install). Windows Server 2016'yı kullanıyorsanız izleyin [Docker Enterprise Edition'ı yüklemek için yönergeler](https://docs.docker.com/install/windows/docker-ee).

## <a name="step-3-switch-to-windows-containers"></a>Adım 3. Kapsayıcılar için Windows geçiş

Yalnızca derleme araçları 2017 gerektiren Windows üzerinde yükleyebilirsiniz [Windows kapsayıcılarına geç](https://docs.docker.com/docker-for-windows/#getting-started-with-windows-containers). Windows 10, Windows kapsayıcıları desteği yalnızca [Hyper-V yalıtım](https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/hyperv-container), Windows Server 2016 üzerinde Windows kapsayıcıları her iki Hyper-V desteği ve işlem yalıtım.

## <a name="step-4-expand-maximum-container-disk-size"></a>4. adımı. En fazla kapsayıcı disk boyutunu genişletin

Visual Studio derleme araçları - ve bir büyük ölçüde, Visual Studio - yüklü için tüm araçları çok sayıda disk alanı gerektirir. Örnek Dockerfile paket önbelleğini devre dışı bırakır, ancak gerekli alanı uyum sağlamak için kapsayıcı görüntülerini disk boyutunu artırılması gerekir. Şu anda Windows üzerinde yalnızca disk boyutu Docker yapılandırmasını değiştirerek artırabilirsiniz.

**Windows 10**:

1. [Docker için Windows simgesine sağ tıklayın](https://docs.docker.com/docker-for-windows/#docker-settings) sistem tepsisi tıklayıp **ayarları**.
2. [' A tıklayın, arka plan programı](https://docs.docker.com/docker-for-windows/#docker-daemon) bölümü.
3. [İki durumlu **temel** ](https://docs.docker.com/docker-for-windows/#edit-the-daemon-configuration-file) düğmesi **Gelişmiş**.
4. (Daha fazla derleme araçları için yeterli büyümek için yeriniz olan) 120 GB disk alanı artırmak için aşağıdaki JSON dizisi özelliği ekleyin.

   ```json
   {
     "storage-opts": [
       "size=120GB"
     ]
   }
   ```

   Bu özellik zaten sahip olduğunuz bir şey eklenir. Örneğin, varsayılan arka plan programı yapılandırma dosyasına uygulanan bu değişiklikler sayesinde, artık görmeniz gerekir:

   ```json
   {
     "registry-mirrors": [],
     "insecure-registries": [],
     "debug": true,
     "experimental": true,
     "storage-opts": [
       "size=120GB"
     ]
   }
   ```

5. Tıklayın **uygulamak**.

**Windows Server 2016**:

1. "Docker" hizmetini durdurun:

   ```shell
   sc.exe stop docker
   ```

2. Yükseltilmiş bir komut isteminden "% ProgramData%\Docker\config\daemon.json" Düzenle (veya ne için belirtilen `dockerd --config-file`).
3. (Daha fazla derleme araçları için yeterli büyümek için yeriniz olan) 120 GB disk alanı artırmak için aşağıdaki JSON dizisi özelliği ekleyin.

   ```json
   {
     "storage-opts": [
       "size=120GB"
     ]
   }
   ```

   Bu özellik zaten sahip olduğunuz bir şey eklenir.
4. Dosyayı kaydedin ve kapatın.
5. "Docker" hizmetini başlatın:

   ```shell
   sc.exe start docker
   ```

## <a name="step-5-create-and-build-the-dockerfile"></a>5. adımı. Oluşturma ve Dockerfile'ı oluşturma

Aşağıdaki örnek Dockerfile, disk üzerinde yeni bir dosyaya kaydedin. Dosya yalnızca "Dockerfile" ise, varsayılan olarak kabul edilir.

> [!WARNING]
> Bu örnek Dockerfile kapsayıcılarına yüklenemez önceki Windows SDK yalnızca dışlar. Önceki sürümlerde, derleme komutunun başarısız olmasına neden.

1. Bir komut istemi açın.
2. (Önerilen) yeni bir dizin oluşturun:

   ```shell
   mkdir C:\BuildTools
   ```

3. Bu yeni dizine dizinleri değiştirin:

   ```shell
   cd C:\BuildTools
   ```

3. Aşağıdaki içeriğe C:\BuildTools\Dockerfile için kaydedin.

   ```dockerfile
   # escape=`

   # Use the latest Windows Server Core image with .NET Framework 4.7.1.
   FROM microsoft/dotnet-framework:4.7.1

   # Restore the default Windows shell for correct batch processing below.
   SHELL ["cmd", "/S", "/C"]

   # Download the Build Tools bootstrapper.
   ADD https://aka.ms/vs/15/release/vs_buildtools.exe C:\TEMP\vs_buildtools.exe

   # Install Build Tools excluding workloads and components with known issues.
   RUN C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache `
       --installPath C:\BuildTools `
       --all `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.10240 `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.10586 `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.14393 `
       --remove Microsoft.VisualStudio.Component.Windows81SDK `
    || IF "%ERRORLEVEL%"=="3010" EXIT 0

   # Start developer command prompt with any other commands specified.
   ENTRYPOINT C:\BuildTools\Common7\Tools\VsDevCmd.bat &&

   # Default to PowerShell if no other command specified.
   CMD ["powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]
   ```

   > [!WARNING]
   > Görüntünüzü doğrudan microsoft/windowsservercore üzerinde temel alıyorsa, .NET Framework düzgün yüklenmeyebilir ve herhangi bir yükleme hata gösterilir. Yükleme tamamlandıktan sonra yönetilen kod çalışmayabilir. Görüntünüzü bunun yerine, temel [microsoft/dotnet-framework:4.7.1](https://hub.docker.com/r/microsoft/dotnet-framework) veya üzeri. Daha sonra PowerShell varsayılan olarak kullanabilir veya bu görüntüleri etiketli sürümü 4.7.1 unutmayın `SHELL` neden olacak `RUN` ve `ENTRYPOINT` başarısız için yönergeler.
   >
   > Visual Studio 2017 sürüm 15,8 veya öncesi (herhangi bir ürünü) üzerinde mcr düzgün yüklenmez<span></span>.microsoft\.com\/windows\/servercore:1809 veya üzeri. Herhangi bir hata görüntülenir.
   >
   > Bkz: [bilinen sorunlar kapsayıcılar için](build-tools-container-issues.md) daha fazla bilgi için.

4. Bu dizinin içinde aşağıdaki komutu çalıştırın.

   ```shell
   docker build -t buildtools2017:latest -m 2GB .
   ```

   Bu komut Dockerfile 2 GB bellek kullanarak geçerli dizinde oluşturur. Bazı iş yükleri yüklenirken varsayılan 1 GB yeterli değildir; Ancak, yalnızca 1 GB bellek, derleme gereksinimlerinize bağlı olarak ile derlemeniz mümkün olabilir.

   Son görüntü etiketli "buildtools2017:latest" olduğundan, hiçbir etiket belirtilirse "son" etiketi varsayılan olduğundan kolayca bir kapsayıcıda "buildtools2017" çalıştırabilirsiniz. Daha belirli bir Visual Studio derleme araçları 2017 sürümüne kullanmak istiyorsanız [Gelişmiş senaryo](advanced-build-tools-container.md), bunun yerine belirli bir kapsayıcıda etiketi Visual Studio, sayı olarak "son" belirli bir kapsayıcı kullanabilmeniz için derleme Sürüm tutarlı bir şekilde.

## <a name="step-6-using-the-built-image"></a>6. adım. Oluşturulan görüntüyü kullanarak

Görüntü oluşturduğunuza göre etkileşimli ve otomatik yapılara yapmak için bir kapsayıcı içinde çalıştırabilirsiniz. Örneğin, yol ve diğer ortam değişkenlerine zaten yapılandırılmış Geliştirici komut istemi kullanır.

1. Bir komut istemi açın.
2. Kapsayıcı tüm geliştirici ile bir PowerShell ortamı başlatmak için ayarlanan ortam değişkenlerine çalıştırın:

   ```shell
   docker run -it buildtools2017
   ```

CI/CD akışınız için bu görüntüyü kullanmak için kendi değerlerinizle yayımlayabilirsiniz [Azure Container Registry](https://azure.microsoft.com/services/container-registry) veya diğer iç [Docker kayıt defteri](https://docs.docker.com/registry/deploying) sunucuları yalnızca bu çekme gerek.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Kapsayıcılar için İleri Düzey Örnek](advanced-build-tools-container.md)
* [Kapsayıcılar için Bilinen Sorunlar](build-tools-container-issues.md)
* [Visual Studio derleme araçları 2017 iş yükü ve Bileşen kimlikleri](workload-component-id-vs-build-tools.md)
