---
layout: post
title: Ocultar versão do Nginx no Linux
date:   2020-07-07 22:5:08 +0530
categories: Servidor
---

Por padrão a versão do Nginx é exibida quando você consulta cabeçahos HTTP ou verifica a saída de erro. 

Um exemplo simples de pesquisa, é executar:

```bash
curl -I https://your-domain
```

Aliás, a saída do comando acima, também mostra versões do Apache. 

![erro nginx](/images/nginx.jpg)

Como você pode observar na saída de erro da imagem, temos a versão do servidor, o que é uma falha de segurança. 

### Como desativar
Para desativar esta informação. Edite o arquivo:

```bash
sudo vim /etc/nginx/nginx.conf
```

Defina:

```bash
server_tokens off;
```

Basicamente o arquivo fica parecido com isto:

```bash
http {
        ## Basic Settings ##
        charset utf-8;
        sendfile on;
        tcp_nopush on;
        tcp_nodelay on;
        log_not_found off;
        keepalive_timeout 65;
        types_hash_max_size 2048;
        client_max_body_size 16M;
        include /etc/nginx/mime.types;
        default_type application/octet-stream;
        ## Hide Nginx version ##
        server_tokens   off;
        ## Security headers for Nginx ## 
        add_header Strict-Transport-Security "max-age=15768000" always;
        add_header X-Content-Type-Options "nosniff" always;
        add_header X-Frame-Options "SAMEORIGIN" always;
        add_header X-Xss-Protection "1; mode=block" always;
        add_header Referrer-Policy  strict-origin-when-cross-origin;
        add_header Feature-policy "accelerometer 'none'; camera 'none'; geolocation 'none'; gyroscope 'none'; magnetometer 'none'; microphone 'none'; payment 'none'; usb 'none'";
        add_header Content-Security-Policy   "default-src 'self' http: https: data: blob: 'unsafe-inline'" always;
        ## SSL Settings ##
        ssl_protocols TLSv1.3;
        access_log /var/log/nginx/access.log;
        error_log /var/log/nginx/error.log;
        ## Virtual Host Configs ##
        include /etc/nginx/conf.d/*.conf;
        include /etc/nginx/sites-enabled/*;
}
```

Reinicie o nginx:

```bash
sudo nginx -t
sudo nginx -s reload
```


### Conclusão
Neste artigo abordo como ocultar a versão do nginx no linux ou Unix. É sempre uma boa pedida, criar a politica de obscuridade. No entanto, manter um firewall ativo e buscar sempre atualizações de segurança é fundamental para que tudo ocorra bem.



### Veja também:
- [Meus cursos](https://profjulianoramos.github.io/cursos/)
- [Meu currículo](https://profjulianoramos.github.io/curriculo/)
- [Aula particular e consultoria](https://profjulianoramos.github.io/consultoria/)


Commits
- 2020-07-07 22:5:08 +0530 - Upload da publicação