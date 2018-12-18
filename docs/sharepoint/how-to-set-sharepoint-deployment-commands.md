---
title: 'Nasıl yapılır: SharePoint dağıtım komutlarını ayarlama | Microsoft Docs'
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
- SharePoint development in Visual Studio, deploying
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 060acd0164ff7819d2abfb8d92f2394b4bcc0672
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37120671"
---
# <a name="how-to-set-sharepoint-deployment-commands"></a>Nasıl yapılır: kümesi SharePoint dağıtım komutlarını
  Dağıtım öncesi ve dağıtım sonrası Komutlar ayarlayarak, dağıtım işlemi özelleştirebilirsiniz. SharePoint çözümlerini Visual Studio'da hata ayıklarken önce ve sonra diğer dağıtım eylemleri şu komutları çalıştırın.  
  
### <a name="to-add-a-pre-deployment-command"></a>Dağıtım öncesi komut eklemek için  
  
1.  Menü çubuğunda seçin **proje** > **\<*ProjectName*> Özellikler**.  
  
2.  Seçin **SharePoint** sekmesi.  
  
3.  İçinde **dağıtım öncesi komut satırı** metin kutusuna, bu adımı özelleştirmek için MS-DOS veya MSBuild komut girin.  
  
     Dizin içeriği dağıtım tamamlanmadan önce listelemek için örneğin **dir**.  
  
### <a name="to-add-a-post-deployment-command"></a>Bir dağıtım sonrası komut eklemek için  
  
1.  Menü çubuğunda seçin **proje** > **\<*ProjectName*> Özellikler**.  
  
2.  Seçin **SharePoint** sekmesi.  
  
3.  İçinde **dağıtım sonrası komut satırı** metin kutusuna, bu adımı özelleştirmek için MS-DOS veya MSBuild komut girin.  
  
     Dağıtım tamamlandıktan sonra dizin içeriği listelemek için örneğin **dir**. Derlemenin derleme dizinden kopyalamak için bir MSBuild değişken kullanmak için girin **$(TargetPath) c:\DeploymentDirectory kopyalama**.  
  
## <a name="see-also"></a>Ayrıca bkz.
 [Paket ve SharePoint çözümlerini dağıtma](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
