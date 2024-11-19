---
layout: default
title: Admission Controllers
nav_order: 1
parent: Güvenlik
---

# Admission Controllers

Kubernetes admission controller'ları, Kubernetes API sunucusuna gelen istekleri, kalıcı hale getirilmeden önce ancak kimlik doğrulama ve yetkilendirmeden sonra yakalayıp işleyen güçlü bir özelliktir. Bu controller'lar, küme yöneticisinin belirlediği kurallara göre istekleri kabul edebilir, reddedebilir veya değiştirebilir.

Kubernetes, çeşitli admission controller'lar sunar. Örneğin, **LimitRanger**, bir Namespace içindeki LimitRange nesnesinde belirtilen kısıtlamaları ihlal eden nesneleri doğrular ve gerekirse kaynak istekleri ve limitleri olmayan Pod'lara varsayılan değerler atar.

Kubernetes API sunucusunun işlevselliğini genişletmek için webhooks kullanılabilir. Bu sayede, üçüncü taraf kodlarla kolay entegrasyon sağlanır. Örneğin, **ImagePolicyWebhook**, bir görüntünün kabul edilip edilmeyeceğine karar vermek için kullanılır. Benzer şekilde, **MutatingAdmissionWebhook** istekleri değiştirebilirken, **ValidatingAdmissionWebhook** isteklerin kabul edilip edilmeyeceğine karar verir.

Admission controller'lar, kaynak isteklerinin çok yüksek olup olmadığını kontrol etmekten, kullanılan temel görüntülerin güvenli olup olmadığını denetlemeye kadar çeşitli güvenlik ve politika uygulamalarında kullanılır. Bu mekanizma, Kubernetes kümesinin güvenliğini artırmak ve istenmeyen yapılandırmaların önüne geçmek için kritik bir rol oynar. 



# Kaynaklar
https://sysdig.com/blog/kubernetes-admission-controllers/
