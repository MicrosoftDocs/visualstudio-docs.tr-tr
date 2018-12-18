---
title: Uygulama kaynaklarını yönetme (.NET) | Microsoft Docs
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
- msvse_resedit.dlg.SetCustomTool
- msvse_settingsdesigner.err.formatvalue
- msvse_resedit.err.nameblank
- msvse_resedit.err.duplicatename
helpviewer_keywords:
- editors [Visual Studio], Resource Designer
- Resource Designer
- resources [Visual Studio], managing
- Resources page in Project Designer
- resources types, Resource Designer
- application resources [Visual Studio]
- Project Designer, Resources page
ms.assetid: f2582734-8ada-4baa-8a7c-e2ef943ddf7e
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b29f32fa59f719af3efab6901596b682c95a5d57
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49287228"
---
# <a name="managing-application-resources-net"></a>Uygulama Kaynaklarını Yönetme (.NET)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Derlenmemiş, ancak bir uygulamanın parçası olan dosyalar için örnek simge dosyaları ya da ses dosyaları kaynak dosyalarıdır. Bu dosyaları derleme işleminin bir parçası olmadığından, ikili dosyalarınızı yeniden derlemenize gerek kalmadan değiştirebilirsiniz. Uygulamanızı yerelleştirmek planlıyorsanız, tüm dizeler ve uygulamanızı yerelleştirdiğiniz zaman değiştirilmesi gereken diğer kaynaklar için kaynak dosyaları kullanmalısınız.  
  
 .NET Masaüstü uygulamalarındaki kaynaklar hakkında daha fazla bilgi için bkz: [masaüstü uygulamalarında kaynakların](http://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890). C++ Masaüstü uygulamalarındaki kaynaklar hakkında daha fazla bilgi için bkz: [kaynak dosyalarıyla çalışma](http://msdn.microsoft.com/library/2699a539-b369-4b78-80f0-df03eb7b6780).  
  
 Windows Store uygulamaları, bir masaüstü uygulamalarından farklı kaynak modeli kullanır. Windows Store uygulamalarında kaynakları hakkında daha fazla bilgi için bkz. [uygulama kaynakları tanımlama](https://msdn.microsoft.com/library/windows/apps/hh465228.aspx) Windows Geliştirme Merkezi Web sitesinde.  
  
## <a name="working-with-resources"></a>Kaynakları ile çalışma  
 Yönetilen kod projesi içinde proje özellikleri penceresini açın ('nde proje düğümüne sağ tıklayın **Çözüm Gezgini** seçip **özellikleri**, veya tür **proje özellikleri**içinde **hızlı başlatma** penceresinde ya da ALT + ENTER yazın **Çözüm Gezgini** pencere). Seçin **kaynakları** sekmesi. Projenizi değil bir zaten içeren, ekleyin ve farklı türde kaynakların silme ve var olan kaynakları değiştirmek, bir .resx dosyası ekleyebilirsiniz.  
  
 C++ projelerinde kaynaklarla çalışmak nasıl öğrenmek için bkz. [nasıl yapılır: kaynak oluşturma](http://msdn.microsoft.com/library/aad44914-9145-45a3-a7d8-9de89b366716).

