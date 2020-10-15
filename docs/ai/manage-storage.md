---
title: Verileri karşıya yüklemek için depolamaya gözatamıyorum
description: Verileri karşıya yüklemeyi veya modelleri ve günlükleri indirmeyi sağlamak için uzak makinedeki veya Azure dosya paylaşımındaki tüm depolamaya nasıl gözatacağınızı öğrenin.
ms.custom: SEO-VS-2020
author: jillre
ms.author: jillfra
manager: jillfra
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- multiple
ms.openlocfilehash: ae419c67b493ef03b08f6fcf627ad0fbe42ca6d0
ms.sourcegitcommit: 9c57730000d5ced37d3887f3928b17076f49d0f7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2020
ms.locfileid: "92099212"
---
# <a name="browse-storage-to-upload-data-or-download-models-and-logs"></a>Verileri karşıya yüklemek veya modelleri ve günlükleri indirmek için depolamaya gözatamıyorum

Verileri karşıya yüklemeyi veya modelleri ve günlükleri indirmeyi sağlamak için uzak makinedeki veya Azure dosya paylaşımındaki tüm depolamaya gözatabilmeniz gerekir. Ya da, belirli bir iş için günlüklere ve iş çıktılarına erişmek istiyorsanız, bu işlemi iş tarayıcısına de yapabilirsiniz.

## <a name="to-access-all-data-on-the-remote-machine-or-file-share"></a>Uzak makinedeki veya dosya paylaşımındaki tüm verilere erişmek için

1. **Sunucu Gezgini**açın.
2. Uzak makineyi veya Batch AI işlem bağlamını genişletin.
3. **Depolama alanı**' na sağ tıklayın; ardından, **Araştır**' a tıklayın.

    ![depolama](media/manage-storage/browse-storage.png)

## <a name="to-access-job-specific-data-on-the-remote-machine-or-file-share"></a>Uzak makinedeki veya dosya paylaşımındaki işe özgü verilere erişmek için

1. [Iş geçmişini](job-details.md) açın
2. İşi seçin.
3. Bu önemli günlük dosyalarına hızlı erişim için **çalışma klasörü** ' ne veya **stdout/stderr** ' e tıklayın.

    ![depolama](media/manage-storage/job-workingfolder.png)
