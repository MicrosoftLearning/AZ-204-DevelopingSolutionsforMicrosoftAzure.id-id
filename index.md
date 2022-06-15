---
title: Petunjuk Host Online
permalink: index.html
layout: home
ms.openlocfilehash: 8cc220d44fe56f19385b25675c29e391b610db8e
ms.sourcegitcommit: d2d374fffa4fcbf92b9c4bdc9c9ecc470152e033
ms.translationtype: HT
ms.contentlocale: id-ID
ms.lasthandoff: 11/16/2021
ms.locfileid: "145196252"
---
## <a name="content-directory"></a>Direktori Konten

Hyperlink ke masing-masing lab tercantum di bawah ini.

## <a name="labs"></a>Lab

{% assign labs = site.pages | where_exp: "page", "page.url contains '/Instructions/Labs'" %}
| Modul | Laboratorium |
| --- | --- |
{% for activity in labs  %}{% if activity.lab.az204Module %}| {{ activity.lab.az204Module }} | [{{ activity.lab.az204Title }}]({{ site.github.url }}{{ activity.url }}) |
{% endif %}{% endfor %}
