---
title: ShowWebBrowser komutu | Microsoft Docs
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
- view.showwebbrowser
helpviewer_keywords:
- ShowWebBrowser command
- View.ShowWebBrowser command
ms.assetid: c6a4fbd6-8e9d-45cc-8b2f-93990d065e78
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f9bf9668a690347988e3148cf90da69ec3b33ca2
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49171957"
---
# <a name="showwebbrowser-command"></a>ShowWebBrowser Komutu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Tümleşik geliştirme ortamı (IDE) veya IDE dışında içindeki bir Web tarayıcı penceresinde belirttiğiniz URL'yi görüntüler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
View.ShowWebBrowser URL [/new][/ext]  
```  
  
## <a name="arguments"></a>Arguments  
 `URL`  
 Gerekli. Web sitesi için URL (Tekdüzen Kaynak Konum Belirleyicisi).  
  
## <a name="switches"></a>Anahtarlar  
 / Yeni  
 İsteğe bağlı. Sayfayı yeni bir Web tarayıcısı örneğini görüntüleneceğini belirtir.  
  
 /ext  
 İsteğe bağlı. Sayfa IDE dışında varsayılan Web tarayıcısında görüntüleneceğini belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
 Diğer **ShowWebBrowser** komutu **gidin** veya **nav**.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, IDE dışında bir Web tarayıcısında MSDN Online Giriş sayfasında gösterilir. Web tarayıcısının bir örneği zaten açıksa kullanılır; Aksi halde yeni bir örneğini başlattınız.  
  
```  
>View.ShowWebBrowser http://msdn.microsoft.com /ext  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio komutları](../../ide/reference/visual-studio-commands.md)   
 [Komut penceresi](../../ide/reference/command-window.md)   
 [Bul/komut kutusu](../../ide/find-command-box.md)   
 [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)



