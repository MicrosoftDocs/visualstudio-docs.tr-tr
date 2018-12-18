---
title: Kubernetes araçları Öğreticisi | Microsoft Docs
ms.custom: ''
ms.date: 06/08/2018
ms.technology: vs-ide-deployment
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: douge
ms.workload:
- azure
ms.openlocfilehash: 8cf4192ce0f925624dbbe890381d3557f2a27223
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49942939"
---
# <a name="get-started-with-visual-studio-kubernetes-tools"></a>Visual Studio Kubernetes araçları kullanmaya başlayın

Visual Studio Kubernetes araçları Kubernetes hedefleyen kapsayıcılı uygulamaların geliştirilmesini kolaylaştıran yardımcı olur. Visual Studio, Kubernetes dağıtımı, dockerfile'ları ve Helm grafiklerini gibi desteklemek için gereken kod olarak yapılandırma dosyaları otomatik olarak oluşturabilirsiniz. Azure geliştirme alanları kullanarak canlı bir Azure Kubernetes Service (AKS) kümesi kodunuzda hata ayıklamak veya bir AKS kümesi doğrudan yayımlamak Visual Studio içinde.

Bu öğretici, Visual Studio kullanarak Kubernetes desteği olan bir projeye ekleme ve yayımlama için AKS kapsar. Kullanarak öncelikle ilgileniyorsanız [Azure geliştirme alanları](http://aka.ms/get-azds) hata ayıklamak ve test projeniz AKS'de çalışan için atlayabilirsiniz [Azure geliştirme alanları öğretici](https://docs.microsoft.com/azure/dev-spaces/get-started-netcore-visualstudio) yerine.

## <a name="prerequisites"></a>Önkoşullar

Bu yeni işlevselliği yararlanmak için gerekir:

- En son sürümünü [Visual Studio 2017](https://visualstudio.microsoft.com/download) ile *ASP.NET ve web geliştirme* iş yükü.

- [Visual Studio için Kubernetes Araçları](https://aka.ms/get-vsk8stools), ayrı bir indirme olarak kullanılabilir.

- [Windows için docker](https://store.docker.com/editions/community/docker-ce-desktop-windows) geliştirme iş istasyonunuzda yüklü (diğer bir deyişle, Visual Studio'yu çalıştırdığınız), Docker görüntülerinizi oluşturmak istiyorsanız, yerel olarak çalışan Docker kapsayıcıları hata ayıklama veya AKS için yayımlayın. (Docker *değil* derleme ve Azure Dev alanları kullanarak AKS Docker kapsayıcılarında hata ayıklama için gereklidir.)

- AKS için Visual Studio'dan yayımlamak isterseniz (*değil* Azure geliştirme alanları kullanarak AKS içinde hata ayıklama için gerekli):

    1.  [Yayınlama araçları AKS](https://aka.ms/get-vsk8spublish), ayrı bir indirme olarak kullanılabilir.

    1.  Azure Kubernetes hizmeti kümesi. Daha fazla bilgi için [bir AKS kümesi oluşturma](/azure/aks/kubernetes-walkthrough-portal#create-aks-cluster). Mutlaka [kümeye bağlanma](/azure/aks/kubernetes-walkthrough#connect-to-the-cluster) geliştirme istasyonunuzdan.

    1.  Helm CLI geliştirme iş istasyonunuzda yüklü. Daha fazla bilgi için [yükleme Helm](https://github.com/kubernetes/helm/blob/master/docs/install.md).

    1.  AKS kümenizi karşı kullanılarak yapılandırılan helm `helm init` komutu. Bunun nasıl yapılacağı hakkında daha fazla bilgi için bkz. [Helm yapılandırma](/azure/aks/kubernetes-helm#configure-helm).

## <a name="create-a-new-kubernetes-project"></a>Yeni bir Kubernetes projesi oluşturma

Uygun araçları yüklü oluşturduktan sonra Visual Studio'yu başlatın ve yeni bir proje oluşturun. Altında **bulut**, seçin **Kubernetes için kapsayıcı uygulama** proje türü. Bu proje türü seçip **Tamam**.

![Yeni bir Kubernetes uygulama projesi oluşturma işleminin ekran görüntüsü](media/k8s-tools-new-k8s-app.png)

Ardından, web uygulaması oluşturmak için ASP.NET Core türünü seçebilirsiniz. Seçin **Web uygulaması** ve **Tamam**. Normal **Docker desteğini etkinleştir** seçeneği, bu iletişim kutusunda görünmez.  Docker desteği Kubernetes için kapsayıcı uygulaması için varsayılan olarak etkinleştirilir.

![Web uygulaması seçiminin ekran görüntüsü](media/k8s-tools-web-app-selection-screen.png)

## <a name="add-kubernetes-support-to-an-existing-project"></a>Mevcut bir projeyi Kubernetes desteği eklendi

Alternatif olarak, mevcut bir ASP.NET Core web uygulaması projesi Kubernetes desteği ekleyebilirsiniz. Bunu yapmak için proje üzerinde sağ tıklatın ve seçin **Ekle** > **kapsayıcı Düzenleyicisi desteği**.

![Ekran görüntüsü, Ekle kapsayıcı Düzenleyicisi menü öğesi](media/k8s-tools-add-container-orchestrator.png)

İletişim kutusunda, "Kubernetes/Helm" seçip **Tamam**.

![Ekran görüntüsü, Ekle kapsayıcı Düzenleyicisi iletişim kutusu](media/k8s-tools-add-container-orchestrator-dialog-box.PNG)

## <a name="what-visual-studio-creates-for-you"></a>Visual Studio sizin için neler oluşturur

Yeni bir oluşturduktan sonra **Kubernetes için kapsayıcı uygulama** , proje veya varolan bir projeye Kubernetes kapsayıcı Düzenleyicisi desteği ekleme, Kubernetes dağıtımı kolaylaştıran bazı ek dosyalar, projenizdeki görürsünüz.

![Çözüm Gezgini'nin ekran görüntüsü kapsayıcı Düzenleyicisi desteği ekledikten sonra](media/k8s-tools-solution-explorer.png)

Eklenen dosyalar şunlardır:

- Bu web uygulamasını barındıran bir kapsayıcı görüntüsü bir Docker oluşturmanıza olanak sağlayan bir Dockerfile. Gördüğünüz gibi Visual Studio Araçları hata ayıklama ve Kubernetes için dağıtırken bu Dockerfile yararlanır. Docker görüntüsünü doğrudan çalışmayı tercih ederseniz, Dockerfile üzerinde sağ tıklatın ve seçin **Docker görüntüsünü derleme**.

   ![Derleme Docker görüntüsü ekran seçeneği](media/k8s-tools-build-docker-image.png)

- bir Helm grafiği ve bir *grafikleri* klasör. Helm grafiği için Kubernetes dağıtmak için kullanabileceğiniz uygulamanın bu yaml dosyaları oluşturur. Helm hakkında daha fazla bilgi için bkz. [ https://www.helm.sh ](https://www.helm.sh).

- *azds.yaml*. Bu hızlı, yinelemeli bir hata ayıklama deneyimini Azure Kubernetes Service'teki sağlayan Azure geliştirme alanları için ayarları içerir. Daha fazla bilgi için lütfen başvuru [Azure geliştirme alanları belgelerine](https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces).

## <a name="publish-to-azure-kubernetes-service-aks"></a>Azure Kubernetes Service'i (AKS) yayımlama

Yalnızca zaman olduğu gibi tüm bu dosyaları yerinde, Visual Studio IDE yazma ve uygulama kodunuzun hatalarını ayıklamak için kullanabilirsiniz. Ayrıca [Azure geliştirme alanları](http://aka.ms/get-azds) hızla çalıştırın ve kodunuzu bir AKS kümesinde çalışırken hata ayıklamak için. Daha fazla bilgi için lütfen başvuru [Azure geliştirme alanları Öğreticisi](https://docs.microsoft.com/azure/dev-spaces/get-started-netcore-visualstudio)

Bir AKS kümeye doğrudan Visual Studio'dan yayımlayabilirsiniz, istediğiniz şekilde çalışan, koda sahip olduğunuzda.

Bunu yapmak için önce her şeyi açıklandığı yüklediğinizi sağlayamazsanız yapmanız [önkoşulları](#prerequisites) bölümünde yayımlamak için AKS öğesinin altındaki ve bağlantıları verilen tüm komut satırı adımlarını çalıştırın. Ardından, kapsayıcı görüntünüzü Azure Container Registry (ACR) yayımlayan bir yayımlama profili ayarlayın. Ardından AKS ACR'den, kapsayıcı görüntüsü çekin ve kümeye dağıtın.

1. İçinde **Çözüm Gezgini**, sağ tıklayın, *proje* ve **Yayımla**.

   ![Menü öğesi, ekran yayımlama](media/k8s-tools-publish-project.png)

2. İçinde **Yayımla** ekran öğesini **kapsayıcı kayıt defteri** Yayımla olarak hedef ve kapsayıcı kayıt defterinizde seçmek için istemleri takip edin. Bir kapsayıcı kayıt defterinde yoksa seçin **yeni Azure Container Registry oluşturma** Visual Studio'dan oluşturma. Daha fazla bilgi için [kapsayıcınızı Azure Container Registry'ye yayımlama](#publish-your-container-to-azure-container-registry).

   ![Çekme Yayımla hedef ekran görüntüsü](media/k8s-tools-publish-to-acr.png)

3. Çözüm Gezgini içinde tekrar sağ tıklayın, *çözüm* tıklatıp **Azure AKS Yayımla**.

   ![Ekran görüntüsü, Web'de yayımlama Azure AKS menü öğesi](media/k8s-tools-publish-solution.png)

4. Aboneliğiniz ve AKS kümenizi seçin, ACR ile birlikte oluşturduğunuz profili yayımlayabilir. Sonra **Tamam**'a tıklayın.

   ![Ekran görüntüsü, Web'de yayımlama AKS ekranı](media/k8s-tools-publish-to-aks.png)

   Sayfasına yönlendirileceksiniz **Azure AKS Yayımla** ekran.

5. Seçin **yapılandırma Helm** Helm grafikleri sunucusuna yüklemek için kullanılan komut satırı güncelleştirmek için bir bağlantı.

   ![Yapılandırma Helm ekran bağlantı](media/k8s-tools-configure-helm.png)

   Komut satırı güncelleştirmek, farklı Kubernetes bağlamı veya grafik gibi bir ad belirlemek istiyorsanız özel bir komut satırı bağımsız değişken varsa yararlı olur.

   ![Ekran görüntüsü, Helm ekran yapılandırın](media/k8s-tools-helm-configure-screen.png)

6. Dağıtmaya hazır olduğunuzda tıklayın **Yayımla** AKS için uygulamanızı yayımlamak için düğme.

   ![Yayımlama Azure AKS ekrana ekran görüntüsü](media/k8s-tools-publish-screen.png)

Tebrikler! Artık tüm Kubernetes uygulama geliştirme için Visual Studio'nun tüm gücünü kullanabilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

Azure'da Kubernetes geliştirme hakkında daha fazla bilgi edinmek [AKS belgelerini](/azure/aks).

Azure geliştirme alanları hakkında daha fazla bilgi edinmek [Azure geliştirme alanları belgeleri](http://aka.ms/get-azds)
