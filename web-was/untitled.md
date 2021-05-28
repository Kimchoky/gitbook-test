# Apache SSL

## SSL 인증서 발급\(via Gabia\)

* Gabia에서 인증서 구매\(DV : Domains Verified\)
* 웹서버에서 private key 생성

```markup
openssl genrsa -des3 -out happy_gabia.key 2048
```

* 웹서버에서 CSR\(Certification Signing Request\) 생성

```markup
openssl req -new -key happy_gabia.key -out happy_gabia.csr -sha256
```

* Gabia 콘솔에 CSR 값 저장
* 인증방식 선택 : 웹인증
* 요구하는 디렉터리에 인증파일을 넣고 외부에서 접근되는 지 확인
* 이후 인증서를 받으면 웹서버어에 복사 및 세팅한다.

CSR은 인증서를 요구하기 위해 필요하다. 내부에 공개키를 포함하고 있다

KEY는 외부에 노출되어선 안된다.

Root CA 또는 ICA는 CSR을 받아 이 것의 해시값을 자신의 PK로 암호화한다. 공개키로 복호화한 값이 인증서의 해시값과 같다면, CA로부터 인증되었다고 볼 수 있다.  -- 좀 더 확인필요

### 

## Apache multiple SSL Guide

```markup

# Apache 2.2 인 경우만. 이후 버전은 없어도 됨
NameVirtualHost *:443


# SSL Setting sample
<VirtualHost *:443>
DocumentRoot "/home/ec2-user/public_html/moonsan"
ServerName www.happyms.or.kr
ServerAlias happyms.or.kr
SSLEngine on
SSLProtocol all -SSLv2
SSLCipherSuite HIGH:MEDIUM:!aNULL:!MD5:!SEED:!IDEA
SSLCertificateFile /etc/httpd/conf/ssl/2021/www.happyms.or.kr/www.happyms.or.kr.crt
SSLCertificateKeyFile /etc/httpd/conf/ssl/2021/www.happyms.or.kr/www.happyms.or.kr.key
#SSLCertificateChainFile /etc/httpd/conf/ssl/2021/www.happyms.or.kr/ALPHASSL_CA__SHA256__G2.crt
#SSLCACertificateFile /etc/httpd/conf/ssl/2021/www.happyms.or.kr/GLOBALSIGN_ROOT_CA.crt
  <Files ~ "\.(cgi|shtml|phtml|php3?)$">
    SSLOptions +StdEnvVars
  </Files>
  <Directory "/var/www/cgi-bin">
    SSLOptions +StdEnvVars
  </Directory>
BrowserMatch "MSIE [2-5]" \
         nokeepalive ssl-unclean-shutdown \
         downgrade-1.0 force-response-1.0
CustomLog logs/www.happyms.or.kr_ssl_log \
          "%t %h %{SSL_PROTOCOL}x %{SSL_CIPHER}x \"%r\" %b"
</VirtualHost>


# Another domain
<VirtualHost>
...
```

Apache 2.2 이상인 경우 SNI\(Server Name Indication\) 기능이 작동한다. 같은 IP의 서버 내 여러 개의 도메인에 SSL\(TLS\)를 적용할 수 있다.

 만일 매칭되는 HTTPS 서버가 없다면 맨 처음 VHOST로 연결되므로 주의가 필요함.\(NGINX는 마지막 VHOST로 연결된다고 함\)

