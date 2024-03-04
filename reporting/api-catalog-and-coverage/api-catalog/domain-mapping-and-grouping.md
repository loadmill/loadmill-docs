# Domain Mapping and grouping

When multiple domains/ip's represent the same service, they can be grouped into one logical service.\
As a result, all the end-points from all the services will be merged and grouped under specified service-name.\
\
For example, if the hosts`echo1.beeceptor.com` and `echo2.beeceptor.com` are different deployments of the same service, we shall group them together by following the instructions:\


1.  Head to "settings", in the dotted menu at the top-right corner of the screen

    <figure><img src="../../../.gitbook/assets/image (14).png" alt=""><figcaption></figcaption></figure>
2. In "General" Tab, under "Domains to Services", Specify a unique regex that matches the domains you want to group, in addition specify service name for display purposes.\
   ![](<../../../.gitbook/assets/image (12).png>)
3. To apply changes on existing domains, check the box "Apply changes to existing APIs".
4. Click on save

<figure><img src="../../../.gitbook/assets/image (13).png" alt=""><figcaption><p>The result will show the new alias name in the service drop-down at the top-right corner</p></figcaption></figure>

note: Domain mapping can be used to alias individual service names for convenience.
