---
title: Test etmek için ClickOnce uygulamaları dağıtma ve üretim sunucularına teslim etmeden | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce applications, deploying without resigning
- ClickOnce deployment, without resigning
- application updates, ClickOnce
- update location [ClickOnce]
- deploymentProvider tag
- manifests [ClickOnce]
ms.assetid: 1218a98d-1ad5-4eef-95dd-0e0b3c44168c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: abfa170fe0f30cbc4fac941a6d77d0ac8b407f7f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49846596"
---
# <a name="deploy-clickonce-applications-for-testing-and-production-servers-without-resigning"></a>Teslim etmeden ClickOnce uygulamaları için test ve üretim sunucuları dağıtma
Bu makalede ClickOnce bildirimlerini yeniden imzalama veya ClickOnce değiştirmeden birden çok ağ konumundan ClickOnce uygulamalarının dağıtımını sağlayan sürüm 3.5 .NET Framework sunulan bir özelliğidir.  
  
> [!NOTE]
>  Bildirimin hala uygulamaların yeni sürümlerini dağıtmak için tercih edilen yöntemdir. Mümkün olduğunda resigning yöntemini kullanın. Daha fazla bilgi için [ *Mage.exe* (bildirim üretme ve düzenleme aracı)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool).  
  
 Üçüncü taraf geliştiriciler ve ISV'ler de bu özelliği, müşterilerine kendi uygulamalarınızı güncelleştirmeye gerek kolaylaştırmaya tercih edebilirsiniz. Aşağıdaki durumlarda bu özellik kullanılabilir:  
  
-   Bir uygulamanın ilk yüklenmesi için bir uygulama güncelleştirilirken.  
  
-   Uygulamanın bir bilgisayarda yalnızca bir yapılandırma olduğunda. Örneğin, bir uygulama iki farklı veritabanına işaret edecek şekilde yapılandırıldıysa, bu özellik kullanamazsınız.  
  
## <a name="exclude-deploymentprovider-from-deployment-manifests"></a>Dağıtım bildirimlerinden deploymentProvider Dışla  
 .NET Framework 2.0 ve .NET Framework 3.0, çevrimdışı kullanım için sisteme yüklenen herhangi bir ClickOnce uygulaması listelemelidir bir `deploymentProvider` , dağıtım bildiriminde. `deploymentProvider` Güncelleştirme konumu olarak; genellikle adlandırılır, ClickOnce Uygulama güncelleştirmeleri nerede denetler konumdur. Bu gereksinim, birlikte dağıtımlarını imzalamak uygulama yayımcıları için gereken bir satıcıdan veya diğer üçüncü taraf bir ClickOnce uygulamasını güncelleştirmek bir şirket için zorlaştırıyordu. Ayrıca, aynı uygulama aynı ağ üzerinde birden fazla konumdan dağıtmak daha zor kılar.  
  
 .NET Framework 3. 5'te yapılan değişiklikler ile ardından kendi ağ üzerinde uygulamasını dağıtabilirsiniz başka bir kuruluştaki bir ClickOnce uygulamasını sağlamak bir üçüncü taraf mümkündür.  
  
 Bu özelliğin avantajlarından yararlanmak için ClickOnce uygulaması geliştiricileri içermemelidir `deploymentProvider` dağıtım bildirimlerinden. Bu gereksinim, içermemelidir anlamına gelir. `-providerUrl` dağıtım oluşturduğunuzda, bağımsız değişken bildirimlerini Mage.exe ile. Veya dağıtım bildirimleri MageUI.exe ile üretiyorsanız emin olmanız gerekir **başlatma konumu** metin kutusunu **uygulama bildirimi** sekmesinde boş bırakılır.  
  
## <a name="deploymentprovider-and-application-updates"></a>deploymentProvider ve uygulama güncelleştirmeleri  
 .NET Framework 3.5 ile başlayarak, artık belirtmek zorunda bir `deploymentProvider` hem çevrimiçi hem de çevrimdışı kullanım için bir ClickOnce uygulamasını dağıtmak için dağıtım bildiriminde. Bu değişiklik, paket ve kendi başınıza imzalaması, ancak kendi ağları üzerinde uygulamayı dağıtmak için diğer kurumlarla izin gerek duyduğunuz senaryolara senaryosunu destekler.  
  
 Anımsanması gereken önemli nokta olan hariç tutan uygulamalar bir `deploymentProvider` yükleme konumlarını içeren bir güncelleştirme bunların Sevk edene kadar güncelleştirmeler sırasında değiştiremezsiniz `deploymentProvider` yeniden etiketleyin.  
  
 Aşağıda, bu noktayı açıklığa kavuşturmak için iki örnek verilmiştir. İlk örnekte, ilgili olmayan ClickOnce uygulaması yayımlama `deploymentProvider` etiketi ve ondan kullanıcılar sorun http://www.adatum.com/MyApplication/. Uygulamayı bir sonraki güncelleştirmesine yayımlamak istediğiniz kullanmaya karar verirseniz http://subdomain.adatum.com/MyApplication/, bu dağıtım bildiriminde bulunan gösteren hiçbir şekilde http://www.adatum.com/MyApplication/. İkisinden birini yapabilirsiniz:  
  
- Önceki sürümü kaldırmalısınız girmelerini söyleyin ve yeni bir konumdan yeni sürümünü yükleyin.  
  
- Bir güncelleştirme içerir http://www.adatum.com/MyApplication/ içeren bir `deploymentProvider` işaret http://www.adatum.com/MyApplication/. Ardından, daha sonra başka bir güncelleştirme sürüm `deploymentProvider` işaret http://subdomain.adatum.com/MyApplication/.  
  
  İkinci örnekte belirten ClickOnce uygulaması yayımlama `deploymentProvider`, ve ardından bunu kaldırmaya karar verirsiniz. Bir kez yeni sürümü olmadan `deploymentProvider` indirilir istemciler için olan uygulama sürümünü bırakana kadar güncelleştirmeleri için kullanılan yolu yönlendiremez `deploymentProvider` geri. İlk örnek olarak, `deploymentProvider` başlangıçta, yeni konum geçerli güncelleştirme konumuna işaret etmelidir. Bu durumda, eklemeyi denerseniz bir `deploymentProvider` başvuran için http://subdomain.adatum.com/MyApplication/, İleri güncelleştirmeyi başarısız olur.  
  
## <a name="create-a-deployment"></a>Bir dağıtım oluşturun  
 Farklı ağ konumlarını dağıtılabilir dağıtımları oluşturma adım adım yönergeler için bkz. [izlenecek yol:, yeniden imzalama gerektirmeyen ve marka bilgisinikoruyanbirClickOnceuygulamasınıeliledağıtma](../deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required.md).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [*Mage.exe* (bildirim üretme ve düzenleme aracı)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)   
 [*MageUI.exe* (bildirim üretme ve düzenleme aracı, grafik istemci)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)