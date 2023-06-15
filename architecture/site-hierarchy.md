# Site Hierarchy

### Domain

{% hint style="success" %}
forms.sbs
{% endhint %}

### Subdomains

1. **mail** -> managed by k8s
2. **dev** -> managed by k8s
3. **did** -> managed by k8s
4. **docs** -> managed by Gitbook

### SSL Certificates

1. https://forme.sbs -> secured by NameCheap SSL
2. https://dev.forme.sbs -> secured by NameCheap SSL
3. https://did.forme.sbs -> secured by NameCheap SSL
4. https://docs.forme.sbs -> secured by GitBook

### DNS

DigitalOcean DNS nameservers used for **forme.sbs** and all subdomains.

Digital Ocean LoadBalancer and nginx ingress used for routing.
