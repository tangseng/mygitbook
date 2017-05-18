# DNS

DNS（Domain Name System，域名系统），最初，由于ip长且难记，通过ip访问网站不方便。。所以后来通过发明了DNS服务器，这个时候我们访问网站输入网站域名，DNS服务器就解析我们的域名为ip。这样我们实际访问的就是对应的ip地址啦。

        dig +trace www.xiuzan.com

        ; <<>> DiG 9.8.3-P1 <<>> +trace www.xiuzan.com
        ;; global options: +cmd
        .			15505	IN	NS	h.root-servers.net.
        .			15505	IN	NS	d.root-servers.net.
        .			15505	IN	NS	m.root-servers.net.
        .			15505	IN	NS	i.root-servers.net.
        .			15505	IN	NS	b.root-servers.net.
        .			15505	IN	NS	a.root-servers.net.
        .			15505	IN	NS	e.root-servers.net.
        .			15505	IN	NS	c.root-servers.net.
        .			15505	IN	NS	l.root-servers.net.
        .			15505	IN	NS	k.root-servers.net.
        .			15505	IN	NS	f.root-servers.net.
        .			15505	IN	NS	j.root-servers.net.
        .			15505	IN	NS	g.root-servers.net.
        ;; Received 228 bytes from 10.0.1.35#53(10.0.1.35) in 32 ms

        com.			172800	IN	NS	a.gtld-servers.net.
        com.			172800	IN	NS	h.gtld-servers.net.
        com.			172800	IN	NS	g.gtld-servers.net.
        com.			172800	IN	NS	l.gtld-servers.net.
        com.			172800	IN	NS	b.gtld-servers.net.
        com.			172800	IN	NS	c.gtld-servers.net.
        com.			172800	IN	NS	f.gtld-servers.net.
        com.			172800	IN	NS	k.gtld-servers.net.
        com.			172800	IN	NS	d.gtld-servers.net.
        com.			172800	IN	NS	j.gtld-servers.net.
        com.			172800	IN	NS	m.gtld-servers.net.
        com.			172800	IN	NS	e.gtld-servers.net.
        com.			172800	IN	NS	i.gtld-servers.net.
        ;; Received 492 bytes from 192.5.5.241#53(192.5.5.241) in 30 ms

        xiuzan.com.		172800	IN	NS	ns1.alidns.com.
        xiuzan.com.		172800	IN	NS	ns2.alidns.com.
        ;; Received 267 bytes from 192.55.83.30#53(192.55.83.30) in 242 ms

        www.xiuzan.com.		600	IN	CNAME	www.xiuzan.com.w.kunlunle.com.
        ;; Received 75 bytes from 140.205.81.11#53(140.205.81.11) in 15 ms


**相关文章**
* [写给前端工程师的DNS基础知识](http://www.sunhao.win/articles/netwrok-dns.html)