---
title: Ayıklama arabirimi yeniden düzenlemesi (C#) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.csharp.refactoring.extractinterface
dev_langs:
- CSharp
helpviewer_keywords:
- refactoring [C#], Extract Interface
- Extract Interface refactoring operation [C#]
ms.assetid: 7d0aa225-3b33-4331-9652-5a67cac6f3d0
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: e7c3af675155cf3d47d82457aadbfb6327895d4f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49279909"
---
# <a name="extract-interface-refactoring-c"></a>Ayıklama Arabirimi Yeniden Düzenlemesi (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ayıklama arabirimi bir varolan bir sınıf, yapı veya arabirim üyeleri ile yeni bir arabirim oluşturmak için kolay bir yol sağlayan bir yeniden düzenleme bir işlemdir.  
  
 Çeşitli istemciler bir sınıf, yapı veya arabirim üyeleri aynı alt kümesi kullandığınızda veya birden çok sınıflar, yapılar veya arabirimleri üyelerin bir alt kümesini ortak olduğunda alt kümesini bir arabirim üyeleri somutlaştırmak yararlı olabilir. Arabirimleri kullanma hakkında daha fazla bilgi için bkz. [arabirimleri](http://msdn.microsoft.com/library/2feda177-ce11-432d-81b4-d50f5f35fd37).  
  
 Ayıklama arabirimi arabirim yeni bir dosya oluşturur ve yeni dosyanın başında imleç yerleştirir. Yeni arabirim, yeni arabirimin adı ve kullanarak oluşturulan dosya adı ayıklamak için hangi üyelerin belirtebilirsiniz **Arabirimi Ayıkla** iletişim kutusu.  
  
### <a name="to-use-extract-interface"></a>Arabirimi Ayıkla kullanmak için  
  
1.  Adlı bir konsol uygulaması oluşturun `ExtractInterface`ve ardından `Program` aşağıdaki kodla  
  
    ```csharp  
    // Invoke Extract Interface on ProtoA.  
    // Note:  the extracted interface will be created in a new file.  
    class ProtoA  
    {  
        public void MethodB(string s) { }  
    }  
    ```  
  
2.  İçinde bulunan imleç ile `MethodB`, tıklatıp **Arabirimi Ayıkla** üzerinde **yeniden düzenleme** menüsü.  
  
     **Arabirimi Ayıkla** iletişim kutusu görüntülenir.  
  
     CTRL + R klavye kısayolunu, ı görüntülemek için de yazabilirsiniz **Arabirimi Ayıkla** iletişim kutusu.  
  
     Ayrıca farenin sağ işaret **yeniden düzenleme**ve ardından **Arabirimi Ayıkla** görüntülenecek **Arabirimi Ayıkla** iletişim kutusu.  
  
3.  Tıklayın **Tümünü Seç**.  
  
4.  **Tamam**'ı tıklatın.  
  
     Yeni dosyanın, IProtoA.cs ve aşağıdaki kodu görürsünüz:  
  
    ```csharp  
    using System;  
    namespace TopThreeRefactorings  
    {  
        interface IProtoA  
        {  
            void MethodB(string s);  
        }  
    }  
    ```  
  
## <a name="remarks"></a>Açıklamalar  
 Bu özellik yalnızca, imleç sınıf, struct veya ayıklamak istediğiniz üyeleri içeren arabirimi konumlandırıldığında erişilebilir. İmleci bu konumda olduğunda, yeniden düzenleme işlemi Arabirimi Ayıkla çağırın.  
  
 Bir sınıf veya yapı çıkartma arabirimi çağırdığınızda tabanları ve arabirimleri listenin yeni arabirim adını içerecek şekilde değiştirilir. Tabanları ve arabirimleri listenin ayıklama bir arabirimde çağırdığınızda değiştirilmez.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yeniden Düzenleme (C#)](../csharp-ide/refactoring-csharp.md)