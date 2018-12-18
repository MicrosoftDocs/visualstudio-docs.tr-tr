---
title: Test etmek için ClickOnce uygulamaları dağıtma ve üretim sunucularına teslim etmeden | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 2b2a26e847a23e8a4037958532889626a931341c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49840044"
---
# <a name="deploying-clickonce-applications-for-testing-and-production-servers-without-resigning"></a>Sınama ve Üretim Sunucuları için Teslim Etmeden ClickOnce Uygulamaları Dağıtma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konuda ele alınmıştır ClickOnce bildirimlerini yeniden imzalama veya ClickOnce değiştirmeden birden çok ağ konumundan ClickOnce uygulamalarının dağıtımını sağlayan sürüm 3.5 .NET Framework tanıtılan yeni bir özelliğidir.  
  
> [!NOTE]
>  Bildirimin hala uygulamaların yeni sürümlerini dağıtmak için tercih edilen yöntemdir. Mümkün olduğunda resigning yöntemini kullanın. Daha fazla bilgi için [Mage.exe (bildirim üretme ve düzenleme aracı)](http://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1).  
  
 Üçüncü taraf geliştiriciler ve ISV'ler için bu özellik, kendi uygulamalarınızı güncelleştirmeye gerek müşterileri kolaylaştırmaya katılımı. Aşağıdaki durumlarda bu özellik kullanılabilir:  
  
-   İlk yükleme haricinde bir uygulamanın bir uygulama güncelleştirilirken.  
  
-   Uygulamanın bir bilgisayarda yalnızca bir yapılandırma olduğunda. Örneğin, bir uygulama iki farklı veritabanına işaret edecek şekilde yapılandırıldıysa, bu özellik kullanamazsınız.  
  
## <a name="excluding-deploymentprovider-from-deployment-manifests"></a>Dağıtım Bildirimleri'nden deploymentProvider hariç tutma  
 .NET Framework 2.0 ve .NET Framework 3.0, çevrimdışı kullanım için sisteme yüklenen herhangi bir ClickOnce uygulaması belirtmelisiniz bir `deploymentProvider` , dağıtım bildiriminde. `deploymentProvider` Güncelleştirme konumu olarak; genellikle adlandırılır, ClickOnce uygulama güncelleştirmelerini denetleyecek konumdur. Uygulama yayımcıları dağıtımlarını imzalamak gerekli ile birlikte bu gereksinim, bir satıcıdan veya diğer üçüncü taraf bir ClickOnce uygulamasını güncelleştirmek bir şirket için zorlaştırıyordu. Ayrıca, aynı uygulama aynı ağ üzerinde birden fazla konumdan dağıtmak daha zor kılar.  
  
 .NET Framework 3. 5'te yapılan değişiklikler ile ardından kendi ağ üzerinde uygulamasını dağıtabilirsiniz başka bir kuruluştaki bir ClickOnce uygulamasını sağlamak bir üçüncü taraf mümkündür.  
  
 Bu özelliğin avantajlarından yararlanmak için ClickOnce uygulaması geliştiricileri içermemelidir `deploymentProvider` dağıtım bildirimlerinden. Bu hariç anlamına gelir `-providerUrl` dağıtım oluşturduğunuzda, bağımsız değişken bildirimlerini Mage.exe veya emin **başlatma konumu** metin kutusunu **uygulama bildirimi** sekmesinde boş bırakılır varsa, dağıtım bildirimleri MageUI.exe ile oluşturduğunuzdan.  
  
## <a name="deploymentprovider-and-application-updates"></a>deploymentProvider ve uygulama güncelleştirmeleri  
 .NET Framework 3.5 ile başlayarak, artık belirtmek zorunda bir `deploymentProvider` hem çevrimiçi hem de çevrimdışı kullanım için bir ClickOnce uygulamasını dağıtmak için dağıtım bildiriminde. Bu paket ve kendi başınıza imzalaması, ancak kendi ağları üzerinde uygulamayı dağıtmak için diğer kurumlarla izin gerek duyduğunuz senaryolara senaryosunu destekler.  
  
 Anımsanması gereken önemli nokta olan hariç tutan uygulamalar bir `deploymentProvider` yükleme konumlarını içeren bir güncelleştirme bunların Sevk edene kadar güncelleştirmeler sırasında değiştiremezsiniz `deploymentProvider` yeniden etiketleyin.  
  
 Aşağıda, bu noktayı açıklığa kavuşturmak için iki örnek verilmiştir. İlk örnekte, ilgili olmayan ClickOnce uygulaması yayımlama `deploymentProvider` etiketi ve ondan kullanıcılar sorun http://www.adatum.com/MyApplication/. Uygulamayı bir sonraki güncelleştirmesine yayımlamak istediğiniz kullanmaya karar verirseniz http://subdomain.adatum.com/MyApplication/, bu dağıtım bildiriminde bulunan gösteren, bir yolu olmaz http://www.adatum.com/MyApplication/. İkisinden birini yapabilirsiniz:  
  
- Önceki sürümü kaldırmalısınız girmelerini söyleyin ve yeni bir konumdan yeni sürümünü yükleyin.  
  
- Bir güncelleştirme içerir http://www.adatum.com/MyApplication/ içeren bir `deploymentProvider` işaret http://www.adatum.com/MyApplication/. Ardından, daha sonra başka bir güncelleştirme sürüm `deploymentProvider` işaret http://subdomain.adatum.com/MyApplication/.  
  
  İkinci örnekte belirten ClickOnce uygulaması yayımlama `deploymentProvider`, ve ardından bunu kaldırmaya karar verirsiniz. Bir kez yeni sürümü olmadan `deploymentProvider` indirildi, istemcilere, uygulamanızın sahip bir sürümün kadar güncelleştirmeler için kullanılan bir yola yönlendirmek mümkün olmayacaktır `deploymentProvider` geri. İlk örnek olarak, `deploymentProvider` başlangıçta, yeni konum geçerli güncelleştirme konumuna işaret etmelidir. Bu durumda, eklemeyi denerseniz bir `deploymentProvider` , başvurduğu http://subdomain.adatum.com/MyApplication/, sonraki güncelleştirme işlemi başarısız olur.  
  
## <a name="creating-a-deployment"></a>Bir dağıtımı oluşturma  
 Farklı ağ konumlarını dağıtılabilir dağıtımları oluşturma adım adım yönergeler için bkz. [izlenecek yol: ClickOnce uygulaması söz konusu mu değil gerektiren Re-Signing'el ile dağıtma ve bu korur markalama bilgileri](../deployment/walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Mage.exe (bildirim üretme ve düzenleme aracı)](http://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)   
 [MageUI.exe (Bildirim Oluşturma ve Düzenleme Aracı, Grafik İstemci)](http://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14)



