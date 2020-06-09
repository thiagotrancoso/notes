# Configurar SSL no VirtualHosts no XAMPP por projeto

#### Habilitar os módulos do apache
Dentro da pasta do apache, abra o arquivo `conf/httpd.conf`.
Descomente as linhas abaixo.
```
LoadModule socache_shmcb_module modules/mod_socache_shmcb.so
LoadModule ssl_module modules/mod_ssl.so
Include conf/extra/httpd-ssl.conf
```

#### Gerar a chave e o certificado
Acesse o site: [https://zerossl.com/free-ssl/#self](https://zerossl.com/free-ssl/#self)

Informe o domínio local e clique em **Generate**.

Salve a chave na pasta `D:/xampp/apache/conf/ssl.key` com a extensão `dominio-local.key`.

Salve o certificado na pasta `D:/xampp/apache/conf/ssl.crt` com a extensão `dominio-local.crt`.

Instale o certificado.

#### Configurando um novo VirtualHost
Dentro da pasta do apache, abra o arquivo `conf/extra/httpd-ssl.conf`

Faça uma cópia do bloco de código `<VirtualHost>`.

Altere as linhas do código copiado informando o caminho da chave e do certificado.
```
SSLCertificateFile "D:/xampp/apache/conf/ssl.crt/dominio-local.crt"
SSLCertificateKeyFile "D:/xampp/apache/conf/ssl.key/dominio-local.key"
```

Reinicie o apache.

Pronto!!!

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTQyODAyNzc0Nl19
-->