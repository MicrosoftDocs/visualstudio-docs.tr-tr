---
title: R ve Docker kapsayıcıları
description: Docker kapsayıcıları için R ayarlayabilir ve bunları Visual Studio ile bağlanma nasıl.
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
ms.openlocfilehash: aeb6026bf7f90d07147ef559bdad9feb03e2c005
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "35667138"
---
# <a name="use-docker-containers-with-r-tools-for-visual-studio"></a>Visual Studio için R araçları ile Docker kapsayıcılarını kullanma

Visual Studio (RTVS) sürümünü 1.3 +, yüklemenin yanı sıra için R Araçları [için Docker Windows](https://www.docker.com/docker-windows), Docker kapsayıcıları ile çalışmaya destekler.

## <a name="create-a-container"></a>Bir kapsayıcı oluşturma

1. Seçin **kapsayıcıları** sağ köşesindeki düğme **çalışma alanları** penceresi (**R Araçları** > **Windows**  >  **Çalışma alanları**). Öğeniz yoksa pencere için Docker Windows yüklü ve indirme için bir bağlantı sağlar bildirir. Docker yükleme işlemi bilgisayarın yeniden başlatılmasını gerektirebilir.

    ![Çalışma alanları (VS2017) Visual Studio için R Araçları penceresinde kapsayıcıları komutu](media/container-workspaces-window.png)

1. İçinde **kapsayıcıları** penceresinde **Oluştur**:

    ![Kapsayıcıları penceresinde komutu oluştur](media/containers-window-create.png)

1. İletişim seçip gerekli bilgileri tamamlayın **Oluştur**. Girdiğiniz kimlik bilgileri, ayrıca, daha sonra oturum açtığınızda, Linux üzerinde bir hesap oluşturmak için kullanılır.

    ![Bir kapsayıcı oluştururken bir kapsayıcı adı ve kimlik bilgilerini girme](media/containers-window-create-fill.png)

1. Bu görüntüyü derlemek RTVS biraz zaman alabilir. **Çıkış** Visual Studio'daki gösterir, ilerleme, ancak çok uzun görüntü sırasında yapmadan görünmesine indirdiğinden sabırlı olun hazırlıklı olun. Görüntüsü oluşturulur, kapsayıcı RTVS başlar ve görünür sonra **kapsayıcı** penceresi. Doğru Durdur denetimlere kaldırın veya kapsayıcı yeniden başlatın.

    ![Zobrazit okno tamamlanmış bir kapsayıcı gösteriliyor](media/containers-window-created.png)

## <a name="connect-to-a-container"></a>Bir kapsayıcıya bağlanma

1. **Yerel çalışan kapsayıcılar** bölümünü **çalışma alanları** penceresi RTVS arka plan programı 5444 bağlantı noktasında çalışan kapsayıcılar görüntüler. (Bkz [Linux için Uzak R Server](setting-up-remote-r-service-on-linux.md) arka plan programının nasıl yapılandırıldığına ilişkin ayrıntılar için.)

    ![Çalışma alanı penceresini gösteren kullanılabilir kapsayıcıları](media/workspaces-window-running-containers.png)

1. Bir kapsayıcıya bağlanmak için kapsayıcı adına çift tıklayın veya sağ İleri okunu seçin. Bağlandığınızda, gördüğünüz bir **R etkileşimli** penceresi (bkz [R etkileşimli penceresi ile iş](interactive-repl-for-r-in-visual-studio.md)):

    ![Çalışma alanları ve REPL penceresinde bir kapsayıcı için açıldı](media/workspaces-window-container-connected.png)

## <a name="use-custom-built-images"></a>Özel olarak geliştirilmiş görüntülerini kullanma

RTVS algılar ve kapsayıcılar docker dosyasında açıklanan microsoft/rtvs görüntü gibi özel oluşturulan görüntüleri kullanılarak oluşturulan yönetilmesine izin verir. Burada kullanılan temel görüntü rtvs arka plan programı, R 3.4.2 ve önceden yüklenmiş ortak R paketleri vardır. **Not**: kullanıcı adı ve parola gerektiğinde burada gösterilen değiştirin.

```docker
FROM microsoft/rtvs:1.3-ub1604-r3.4.2
RUN useradd --create-home ruser1
RUN echo "ruser1:foobar" | chpasswd

#Install additional R packages. You may have to install OS dependencies, see package info or error messages during build.
#RUN Rscript --vanilla -e "install.packages(c('AzureML','wordcloud'), repos = 'http://cran.us.r-project.org');"
```

Kapsayıcı adının değiştirilmesi bir görüntüsünü oluşturmak için aşağıdaki komutu kullanın ( `--name` bağımsız değişkeni) istenen şekilde:

```bash
docker build -t my-rtvs-image:latest .
docker run -p 6056:5444 --name my-rtvs-container my-rtvs-image:latest rtvsd
```

`-p 6056:5444` Bağımsız değişken eşlemeleri RTVS rtvs arka plan programı algılamak için kullandığı 6056 oluşturun iç bağlantı 5444, bağlantı noktası. Kapsayıcı bağlantı noktasından 5444 sunan herhangi bir kapsayıcı içinde listelenen **çalışma alanları** penceresi. Ardından **çalışma alanları** penceresini kullanarak bir kapsayıcı bağlanmak için `<<unix>>\ruser1` kullanıcı adı ve parola olarak "foobar" olarak docker dosyasında farklı kimlik bilgileri belirtilmediği sürece.
