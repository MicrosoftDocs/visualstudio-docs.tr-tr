---
title: 'Nasıl yapılır: Windows görünümünde pencere arama | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- windows, searching in Windows view
ms.assetid: 30306970-b861-4315-acf8-f86a43d4e73b
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 60eb467a24c85d176dae7727a476cc45dac6c876
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51782979"
---
# <a name="how-to-search-for-a-window-in-windows-view"></a>Nasıl Yapılır: Pencereler Görünümünde Pencere Arama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Arama ölçütü olarak tanıtıcısını, açıklamalı alt yazı, sınıf veya kendi açıklamalı alt yazı ve sınıfı bir bileşimini kullanarak Windows görünümünde belirli bir pencere için arama yapabilirsiniz. İlk arama yönünü de belirtebilirsiniz. İletişim kutusunda alanları penceresi ağacında seçilen pencere özniteliklerini gösterir.  
  
 İkinci düzey (Masaüstü alt öğesi olan tüm windows), genişletilmiş ağaç başlama Masaüstü düzeyinde windows kendi sınıf adı ve başlık olarak belirleyebilir. Bir masaüstü düzeyi penceresi seçtikten sonra belirli bir alt pencere bulmak için bu düzey genişletebilirsiniz.  
  
### <a name="to-search-for-a-window-in-windows-view"></a>Windows görünümünde pencere arama  
  
1.  Bu nedenle pencereleri bu Spy ++, [Windows görünümü](../debugger/windows-view.md) penceresi ve hedef penceresi görünür.  
  
2.  Gelen **arama** menüsünde seçin **Bul penceresi**.  
  
     [Pencere arama iletişim kutusu](../debugger/window-search-dialog-box.md) açılır.  
  
    > [!TIP]
    >  Ekranda kapladığı alanı azaltmak için seçin **Gizle Spy** seçeneği. Bu seçenek ana Spy ++ penceresini gizler ve yalnızca bırakır **arama penceresi** iletişim kutusu, diğer uygulamalar üzerinde görünür. Spy ++ ana pencereyi geri tıkladığınızda **Tamam** veya **iptal**, veya kaldırdığınızda **Gizle Spy ++** seçeneği.  
  
3.  Sürükleme **Bulucu Aracı** hedef aralığında. Aracı sürüklerken **arama penceresi** iletişim kutusunda seçili penceresinde ayrıntılarını görüntüler.  
  
     – veya –  
  
     (Örneğin, hata ayıklayıcı) istediğiniz pencere tanıtıcısı biliyorsanız, bunu yazabilirsiniz **işlemek** kutusu.  
  
     – veya –  
  
     Açıklamalı alt yazı ve/veya istediğiniz pencere sınıfının biliyorsanız bunları yazabilirsiniz **açıklamalı alt yazı** ve **sınıfı** metin kutuları ve clear **işlemek** metin kutusu.  
  
4.  Seçin **yukarı** veya **aşağı** için ilk arama yönünü.  
  
5.  **Tamam**'ı tıklatın.  
  
     Eşleşen bir pencere bulunursa, vurgulanır [Windows görünümü](../debugger/windows-view.md) penceresi.



