# Configurar SSL no VirtualHosts no XAMPP por projeto

Este tutorial vai te mostrar como habilitar o HTTPS para todos os seus projetos que são desenvolvidos em ambiente local.

Ao final desse tutorial você acessará seus projetos como no exemplo abaixo:
https://localhost.test
https://meuprojeto.test
https://gosteidisso.test

## Parte 1
### Baixar o XAMPP
Você pode baixar o instalador ou a versão portable, neste tutorial usarei a versão portable.

**Site para download:**
[https://www.apachefriends.org/pt_br/index.html](https://www.apachefriends.org/pt_br/index.html)

## Parte 2
### Habilitar os módulos do apache
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
eyJoaXN0b3J5IjpbMTc0MzU0NTU5NV19
-->