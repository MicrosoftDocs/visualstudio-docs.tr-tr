---
title: Şekiller ve Bağlayıcıları Tanımlama
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 48000bbf05fd15163c0c6f61ff4a13838aaf75b6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49881748"
---
# <a name="defining-shapes-and-connectors"></a>Şekiller ve Bağlayıcıları Tanımlama
Bir etki alanına özgü dil (DSL) diyagramda hakkındaki bilgileri görüntülemek için kullanılan şekillerinin birkaç temel türü vardır.

##  <a name="shapeTypes"></a> Şekilleri ve bağlayıcıları temel türleri
 Bir DSL diyagramı koleksiyonu gösterir *şekiller* birbirine satırlarla veya *Bağlayıcılar*.  Genellikle, ancak her zaman:

- Şekiller görünür gösterimini model öğeleri var.

- Bağlayıcılar başvurusu ilişkileri temsil eder.

- Diyagram model kök örneğini temsil eder.

- Model öğeler arasındaki katıştırma ilişkileri kapsamlarına göre gösterilir. Örneğin, bileşenin bağlantı noktalarını temsil eden öğe bileşeni katıştırılır.

  Bu düzenleri zorlanmaz ancak daha kesin desteklenir. Bir DSL tasarlarken, tasarım katıştırma ilişkilerinin olmalıdır aklınızda size aittir nasıl model ekranda sunmak istediğiniz tarafından etkiler. Bunun aksine, başvuru ilişkileri iş etki alanınızın kavramları yansıtmalıdır.

  Aşağıdaki şekil türleri kullanılabilir:

|Şekil türü|Açıklama|
|-|-|
|Geometri şekli|Genel amaçlı dikdörtgen veya elips şekli. Metni ve simgesi dekoratörler belirli konumda şeklin sınırları göre görüntüleyebilirsiniz.<br /><br /> Geometrik şekiller içinde şekilleri iç içe yerleştirmek için bkz: [iç içe şekiller](../modeling/nesting-shapes.md).|
|Bölme şekli|Üst bilgi ve bir UML sınıfı gibi bölmeleri içeren dikdörtgen. Her bölme, metni satır listesini içerebilir.<br /><br /> Satırları, genellikle şekil tarafından temsil edilen öğeyi altında katıştırılmış öğeleri temsil eder. Örneğin, sınıf diyagramları çözüm şablonundan bir DSL oluşturun.|
|Görüntü şekli|Resim görüntüleyen şekli.|
|Bağlantı noktası şekli|Küçük bir dikdörtgen için başka bir şeklin ana hat eklemek için tasarlanmıştır. Genellikle, bileşen modellerinde kullanılır.<br /><br /> Bir bağlantı noktası tarafından temsil edilen model öğesi, genellikle üst şeklin tarafından temsil edilen öğeyi altında eklenir. Örneğin, bir DSL bileşenleri çözüm şablonu kullanarak oluşturun.<br /><br /> Varsayılan olarak, bir bağlantı noktası şeklini üst tarafında kaydırabilirsiniz. Belirli bir konuma sınırlamak için bir sınır kural tanımlayabilirsiniz.<br /><br /> Çok küçük ve saydam bir bağlantı noktası şeklini hale getirerek, üst şeklin solunun yüzeyine bir sabit bağlantı noktası sağlamak için kullanabilirsiniz.|
|Kulvarlar|Kulvarlar diyagram parçalara yatay veya dikey bölümleme. Kulvar, her zaman diğer şekillerin diyagram üzerinde altında kalır.<br /><br /> Model kökünde genellikle kulvarın model öğeleri arasındaki shapemap ve diğer öğeleri üzerinde shapemap. Örneğin, Görev akışı çözüm şablonundan bir DSL oluşturun.|
|Bağlayıcılar|Şekiller arasında genellikle çizilmiş satırları başvuru ilişkileri temsil eder. Bir bağlayıcı düz veya dönüşler yapmak ve ok ucu farklı türleri için seçenekleri ayarlayabilirsiniz.|

##  <a name="shapeInheritance"></a> Şekil devralma
 Bir şekli başka bir şekilden devralabilir. Ancak, şekilleri aynı türde olmalıdır. Örneğin, yalnızca geometri şekli geometri şekilden devralabilir. Devralınan şekilleri bölmeleri ve kendi temel şeklin dekoratörler bulunur. Bağlayıcılar bağlayıcılardan devralabilir.