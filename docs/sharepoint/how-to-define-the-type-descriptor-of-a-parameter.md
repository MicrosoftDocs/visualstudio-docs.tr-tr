---
title: 'Nasıl yapılır: bir parametrenin tür tanımlayıcısını tanımlama | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], type descriptor
- BDC [SharePoint development in Visual Studio], parameter types
- BDC [SharePoint development in Visual Studio], type descriptor
- Business Data Connectivity service [SharePoint development in Visual Studio], parameter types
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ec2b0173838446c770f3323aacefebabc195c48b
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51294987"
---
# <a name="how-to-define-the-type-descriptor-of-a-parameter"></a>Nasıl yapılır: bir parametrenin tür tanımlayıcısını tanımlama
  Bir tür tanımlayıcı bir parametrenin veri türünü tanımlayan özellikler içerir. Tür tanımlayıcısını bir alan, bir varlık veya varlık koleksiyonunu tanımlayabilirsiniz. Daha fazla bilgi için [TypeDescriptor](/previous-versions/office/developer/sharepoint-2007/ms543392\(v\=office.12\)).  
  
### <a name="to-define-the-type-descriptor-of-a-parameter"></a>Bir parametrenin tür tanımlayıcısını tanımlamak için  
  
1.  İçinde **BDC yöntem ayrıntıları** penceresinde, parametrenin tür tanımlayıcısını seçin.  
  
2.  Menü çubuğunda, **görünümü**, **Özellikler penceresi**.  
  
3.  İçinde **özellikleri** penceresinde tür tanımlayıcısı özelliklerini ayarlayın.  
  
     Aşağıdaki yordamlarda, bir tür tanımlayıcı bir alanı, varlığı veya varlık koleksiyonu olarak tanımlamak açıklanır.  
  
### <a name="to-define-a-field"></a>Bir alanı tanımlamak için  
  
1.  İçinde **özellikleri** penceresinde **adı** özelliği tür tanımlayıcı bir varlığı temsil eden tür alanı adını (örneğin: **FirstName**).  
  
2.  Listesinde yanında **TypeName** özelliği, uygun veri türünü seçin (örneğin, **Int32**).  
  
     Diğer isteğe bağlı parametreler hakkında daha fazla bilgi için bkz: [TypeDescriptor](/previous-versions/office/developer/sharepoint-2007/ms543392\(v\=office.12\)).  
  
### <a name="to-define-an-entity"></a>Bir varlık tanımlamak için  
  
1.  İçinde **özellikleri** penceresinde **adı** özelliğini varlığı tanımlayan bir ad (örneğin: **kişi**).  
  
2.  Ayarlama **TypeName** özelliğini tam olarak nitelenmiş adını varlığı temsil eden tür. Bu tür bir sınıf projenizi, çözümünüzde başvurduğunuz bir derlemede tanımlı bir tür veya BDC nesne modelinde tanımlı bir tür olabilir.  
  
    -   Projenizdeki bir sınıf için yanındaki aşağı oku seçin **TypeName** özelliği seçin **geçerli proje** sekmede görünür ve ardından projenizdeki sınıfı seçin iletişim kutusu.  
  
         Tam adı ad alanı ve LOB sistemi adından önce gelen sınıfın adını içerir. Aşağıdaki örnekte ayarlar **TypeName** projenizdeki bir sınıf.  
  
         `MyBDCNamespace.BdcModel1.Contact, BdcModel1`  
  
    -   Çözümünüzdeki bir derlemede bulunan bir tür için tam nitelikli ad tür adını, derleme, sürüm numarasını, kültürü ve ortak anahtar belirteci adını içerir.  
  
         Aşağıdaki örnekte ayarlar **TypeName** çözümünüz içerisinde referans bir derlemede tanımlı bir tür özelliği.  
  
         `MyNamespace.Contact, myAssemblyName, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
    -   İVB nesne modelinde tanımlı bir tür için tam adı ad alanı ve tür adını içerir.  
  
         Aşağıdaki örnekte ayarlar **TypeName** BDC nesne modeli içerisindeki bir türe özelliği.  
  
         `Microsoft.BusinessData.Runtime.DynamicType`  
  
3.  İçinde **BDC yöntem ayrıntıları** penceresinde tür tanımlayıcısı için görüntülenen listeyi açın ve ardından **Düzenle**.  
  
     **BDC Gezgini** penceresi açılır.  
  
4.  İçinde **BDC Gezgini**, tür tanımlayıcı kısayol menüsünü açın ve ardından **tür tanımlayıcı Ekle**.  
  
     Yeni bir tür tanımlayıcı alt öğe olarak varlık türü tanımlayıcısına eklenir. Bu tür tanımlayıcıyı alan olarak yapılandırın.  
  
5.  Varlığın her alanı için bir alt tür tanımlayıcısı eklemek için 4. adımı yineleyin.  
  
### <a name="to-define-a-collection-of-entities"></a>Bir varlık koleksiyonu tanımlamak için  
  
1. İçinde **BDC yöntem ayrıntıları** penceresinde, istediğiniz parametrenin tür tanımlayıcısını seçin.  
  
2. Menü çubuğunda, **görünümü**, **Özellikler penceresi**.  
  
3. İçinde **özellikleri** penceresinde **adı** özelliğini varlığı tanımlayan bir ad (örneğin: **kişiler**).  
  
4. Ayarlama **IsCollection** özelliğini **True**. Bu, bu tür tanımlayıcıyı varlıklar koleksiyonu olduğunu gösterir.  
  
5. Ayarlama **TypeName** başvuru içeren bir dize özelliğini <xref:System.Collections.Generic.IEnumerable%601> arabirimi ve türün varlığı temsil eden tam adı. Bu tür bir sınıf projenizi, çözümünüzde başvurduğunuz bir derlemede tanımlı bir tür veya BDC nesne modelinde tanımlı bir tür olabilir.  
  
   - Projenizdeki bir sınıf için yanındaki aşağı oku seçin **TypeName** özelliği seçin **geçerli proje** sekmede görünür ve ardından projenizdeki sınıfı seçin iletişim kutusu.  
  
      Tam adı ad alanı ve LOB sistemi adından önce gelen sınıfın adını içerir.  
  
      Aşağıdaki örnekte ayarlar **TypeName** projeniz içerisindeki sınıflar koleksiyonuna özelliği.  
  
      `System.Collections.Generic.IEnumerable`1 [MyBDCNamespace.` ` BdcModel1.Contact, BdcModel1]'  
  
   - Çözümünüzdeki bir derlemede bulunan bir tür için tam nitelikli ad tür adını, derleme, sürüm numarasını, kültürü ve ortak anahtar belirteci adını içerir.  
  
      Aşağıdaki örnekte ayarlar **TypeName** özelliğini çözümünüz içerisinde referans derlemedeki türleri koleksiyonu.  
  
      `System.Collections.Generic.IEnumerable`1 [MyNamespace.Contact, myAssemblyName, sürüm 4.0.0.0, Culture = neutral, PublicKeyToken = b77a5c561934e089]'  
  
   - İVB nesne modelinde tanımlı bir tür için tam nitelikli ad yalnızca ad alanı ve tür adını içerir.  
  
      Aşağıdaki örnekte ayarlar **TypeName** BDC nesne modeli içerisinde belirlenen türler koleksiyonuna özelliği.  
  
      `System.Collections.Generic.IEnumerable`1 [Microsoft.BusinessData.Runtime.DynamicType]'  
  
6. İçinde **BDC yöntem ayrıntıları** penceresinde tür tanımlayıcısı için görüntülenen listeyi açın ve ardından **Düzenle**.  
  
    **BDC Gezgini** penceresi açılır.  
  
7. İçinde **BDC Gezgini**, tür tanımlayıcı kısayol menüsünü açın ve ardından **tür tanımlayıcı Ekle**.  
  
    Yeni bir tür tanımlayıcı alt öğe olarak koleksiyon türü tanımlayıcısına eklenir. Bu tür tanımlayıcıyı varlık olarak yapılandırın.  
  
## <a name="see-also"></a>Ayrıca bkz.
 [BDC modeli tasarım araçlarına genel bakış](../sharepoint/bdc-model-design-tools-overview.md)   
 [Nasıl yapılır: modele bir varlık ekleme](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [Nasıl yapılır: bir yönteme bir parametre ekleyin](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Nasıl yapılır: bir yöntemi örneği tanımlama](../sharepoint/how-to-define-a-method-instance.md)   
 [İş verileri bağlantı modeli tasarlama](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
