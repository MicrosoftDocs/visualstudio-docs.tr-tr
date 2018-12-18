---
title: Çağrı hiyerarşisi | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.CallHierarchy
helpviewer_keywords:
- Call Hierarchy
ms.assetid: c55bda01-d7de-4823-8f9a-1bcc37dbb74a
caps.latest.revision: 45
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 86cf4e12f412e6448f4a4b7c38af8268f10d9c56
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49851133"
---
# <a name="call-hierarchy"></a>Çağrı Hiyerarşisi
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Çağrı hiyerarşisini seçili yöntemi, özelliği veya Oluşturucu gelen ve giden tüm çağrıları görüntüleyerek kodunuza gitmenizi sağlar. Bu, daha iyi kodun nasıl aktığını anlamak ve kod değişikliklerinin etkilerini değerlendirilecek sağlar. Kod yöntem çağrıları ve tüm olası yürütme yolları keşfetmenize olanak sağlar koda ek giriş noktaları karmaşık zincirleri görüntülemek için çeşitli düzeylerde inceleyebilirsiniz.  
  
 Çağrı hiyerarşisini, tasarım zamanında hata ayıklayıcı tarafından görüntülenen çağrı yığınını farklı olarak kullanılabilir.  
  
## <a name="using-call-hierarchy"></a>Çağrı hiyerarşisi kullanma  
 Görüntülenecek **çağrı hiyerarşisi** penceresinde bir yöntemi, özelliği veya oluşturucu çağrısı adına sağ tıklayın ve ardından **çağrı hiyerarşisini**.  
  
 Üye adı bir ağaç görünümü bölmesinde görünür **çağrı hiyerarşisi** penceresi. Üye düğümünü genişletirseniz **çağrıları için**_üye adı_ ve **gelen çağrıları**_üye adı_ düğümlerinde görünür. Bu düğümler aşağıdaki çizimde **çağrı hiyerarşisi** penceresi.  
  
 ![Çağrı hiyerarşisi açık bir düğümle](../../ide/reference/media/onenode.png "OneNode")  
Çağrı hiyerarşisi penceresi  
  
- Genişletirseniz **çağrıları için** düğüm, tüm üyeleri seçilen üyenin çağrı görüntülenir.  
  
- Genişletirseniz **gelen çağrıları** düğümü, seçilen üye tarafından çağrılan tüm üyeleri görüntülenir.  
  
  Ardından her biri bu alt düğüm üyeleri genişletebilirsiniz **çağrıları için** ve **gelen çağrıları** düğümleri. Bu, Arayanların, yığına gitmek aşağıdaki çizimde gösterildiği gibi sağlar.  
  
  ![Çağrı hiyerarşisi birden çok düğüm açık](../../ide/media/multiplenodes.png "MultipleNodes")  
  Çağrı hiyerarşisi penceresi  
  
  Sanal veya soyut olarak tanımlanan üyeler için bir **geçersiz kılmaları yöntem adı** düğümü görüntülenir. Arabirim üyeleri için bir **uygulayan yöntem adı** düğümü görüntülenir. Bu Genişletilebilir düğümler aynı seviyede görünür **çağrıları için** ve **gelen çağrıları** düğümleri.  
  
  **Arama kapsamı** araç çubuğundaki seçenekleri içeren **My çözüm**, **geçerli proje**, ve **geçerli belge**.  
  
  Bir alt üye seçtiğinizde **çağrı hiyerarşisi** ağaç görünümü bölmesinde:  
  
- **Çağrı hiyerarşisi** Ayrıntılar bölmesinde, tüm alt üyenin üst üyesi çağrıldığında kod satırlarını görüntüler.  
  
- **Kod tanımı penceresi**, açıksa, kod için seçilen üyenin adını görüntüler. Bu pencere, C# ve C++ dillerinde kullanılabilir. Bu pencere hakkında daha fazla bilgi için bkz. [Structure of Code görüntüleme](../../ide/viewing-the-structure-of-code.md).  
  
> [!NOTE]
>  Çağrı hiyerarşisi grubu başvuruları burada bir yöntem bir olay işleyicisi eklenir veya bir temsilciye atanmış basamak içeren yöntemi bulmaz. Bir yöntem için tüm başvuruları Bul için kullanabileceğiniz **tüm başvuruları Bul** komutu.  
  
## <a name="shortcut-menu-items"></a>Kısayol menü öğesi  
 Aşağıdaki tabloda, bir düğüm ağaç görünümü bölmesinde sağ tıklattığınızda, kullanılabilen birkaç kısayol menü seçenekleri açıklanmaktadır.  
  
|Bağlam menüsü öğesi|Açıklama|  
|-----------------------|-----------------|  
|**Yeni kök olarak Ekle**|Seçili düğüm için ağaç görünümü bölmesinde yeni bir kök düğümü ekler. Bu belirli bir alt ağaçta ilgilenmeniz odaklanmanızı sağlar.|  
|**Kökü Kaldır**|Ağaç görünümü bölmesinde seçilen kök düğümü kaldırır. Bu seçenek, yalnızca bir kök düğümü kullanılabilir.<br /><br /> Ayrıca **kaldırmak kök** araç çubuğu düğmesi seçili kök düğümü kaldırmak için.|  
|**Tanıma Git**|Seçili düğümde Tanıma Git komutu çalıştırır. Bu, bir üye çağrısı için orijinal tanımını veya değişken tanımını gider.<br /><br /> Tanıma Git komutu çalıştırmak için Seçili düğüme çift tıklayın veya seçili düğümde F12 tuşuna basın.|  
|**Tüm başvuruları Bul**|Seçili düğümde tüm başvuruları Bul komutu çalıştırır. Bu kod satırlarını projenize bu başvuruyu bir sınıf veya üye bulur.<br /><br /> Seçili düğümde tüm başvuruları Bul komutu çalıştırmak için SHIFT + F12 de kullanabilirsiniz.|  
|**Kopyala**|Seçili düğümü (ancak alt düğümlerini) içeriğini kopyalar.|  
|**Yenileme**|Böylece geçerli bilgilerini görüntüler yeniden genişleterek seçili düğümü daraltır.|



