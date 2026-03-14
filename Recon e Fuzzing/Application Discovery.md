# APPLICATION DISCOVERY

Application Discovery é a fase onde deixamos de olhar apenas o domínio e passamos a mapear:

- URLs existentes
    
- Rotas internas
    
- Arquivos
    
- Parâmetros
    
- Endpoints de API
    
- JavaScript exposto
    
- Diretórios ocultos
    

Ela se divide em três grandes blocos:

1. URL Discovery
    
2. Content Discovery
    
3. Parameter Discovery
    

---

# 1. URL DISCOVERY

URL Discovery busca coletar todas as URLs conhecidas de um domínio ou subdomínio.

Exemplo:

```
https://empresa.com/login
https://empresa.com/api/v1/user
https://empresa.com/admin/panel
https://empresa.com/uploads/backup.zip
```

Mesmo que não estejam linkadas na página principal, podem existir em:

- Wayback
    
- JavaScript
    
- Histórico
    
- Certificados
    
- APIs públicas
    

---

## GAU (GetAllURLs)

Repositório:  
[https://github.com/lc/gau](https://github.com/lc/gau)

![Image](https://miro.medium.com/v2/resize%3Afit%3A1400/1%2AhNEdASdnbOpO4sExItbpAQ.jpeg)

![Image](https://opengraph.githubassets.com/25ea9ff97a7c40e4fdc514e6a3be8a4990171835a75bd3664315ff86e03deedf/tomjbast/getAllUrls)

![Image](https://media2.dev.to/dynamic/image/width%3D1000%2Cheight%3D420%2Cfit%3Dcover%2Cgravity%3Dauto%2Cformat%3Dauto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2Fg6u7ulnj4ih1za7z7zwv.jpeg)

![Image](https://user-images.githubusercontent.com/103888143/163716433-1d590c9a-ae0d-426b-a50d-cb883e7eb0da.jpg)

### O que é

GAU coleta URLs de diversas fontes públicas:

- Wayback Machine
    
- Common Crawl
    
- OTX
    
- URLScan
    

Ele não faz ataque. Apenas coleta URLs já conhecidas publicamente.

---

## Instalação no Kali Linux

GAU é escrito em Go.

### Instalar Go (se necessário)

```bash
sudo apt update
sudo apt install golang -y
```

Verificar:

```bash
go version
```

---

### Instalar GAU

```bash
go install github.com/lc/gau/v2/cmd/gau@latest
```

O binário será instalado em:

```
~/go/bin/gau
```

---

## Tornar executável de qualquer lugar

Para rodar de qualquer diretório:

### Opção 1 – Adicionar ao PATH

Edite:

```bash
nano ~/.bashrc
```

Adicione:

```
export PATH=$PATH:~/go/bin
```

Depois:

```bash
source ~/.bashrc
```

Agora você pode rodar:

```bash
gau empresa.com
```

---

### Opção 2 – Mover para /usr/local/bin

```bash
sudo mv ~/go/bin/gau /usr/local/bin/
```

Agora funciona globalmente.

---

## Uso básico

```bash
gau empresa.com
```

Salvar:

```bash
gau empresa.com > urls.txt
```

Filtrar parâmetros:

```bash
gau empresa.com | grep "="
```

---

# Hakrawler

Repositório:  
[https://github.com/hakluke/hakrawler](https://github.com/hakluke/hakrawler)

![Image](https://miro.medium.com/1%2AkpuT3tZ7bS5qSLJPQa_7IQ.png)

![Image](https://www.100security.com.br/images/hakrawler-04.png)

![Image](https://www.openexploit.in/content/images/2025/06/hakrawler-tutorial-fast-web-crawler-for-bug-bounty.png)

![Image](https://miro.medium.com/v2/resize%3Afit%3A1358/format%3Awebp/1%2Aq64vbEOfBALwsXaMhIjbaw.png)

### O que faz

Crawler rápido que:

- Extrai links
    
- Descobre rotas internas
    
- Descobre endpoints JS
    

Instalação:

```bash
go install github.com/hakluke/hakrawler@latest
```

Uso:

```bash
echo https://empresa.com | hakrawler
```

---

# WFuzz

Repositório:  
[https://github.com/xmendez/wfuzz](https://github.com/xmendez/wfuzz)

![Image](https://www.kali.org/tools/wfuzz/images/wfuzz-logo.svg)

![Image](https://www.researchgate.net/publication/368804290/figure/fig3/AS%3A11431281122434062%401677336040921/Using-Wfuzz-for-finding-for-finding-pair-login-password.jpg)

![Image](https://www.researchgate.net/publication/368804290/figure/fig2/AS%3A11431281122445190%401677336040768/Using-Wfuzz-for-login-finding.ppm)

![Image](https://miro.medium.com/v2/resize%3Afit%3A1248/1%2AbITdyQOvZsxQisIfE0u8zw.png)

Ferramenta de fuzzing HTTP.

Instalação no Kali:

```bash
sudo apt install wfuzz -y
```

Uso básico:

```bash
wfuzz -u https://empresa.com/FUZZ -w wordlist.txt
```

---

# FFUF

Repositório:  
[https://github.com/ffuf/ffuf](https://github.com/ffuf/ffuf)

![Image](https://codingo.com/images/ffuf/ffuf-extension-hits.png)

![Image](https://miro.medium.com/v2/resize%3Afit%3A1400/1%2AULW69Pa1lukURkGNcgQiYw.png)

![Image](https://camo.githubusercontent.com/54a0b5edac7a822a1c4cc72fe316116309cf085bc3e5fefac1a2fc97d3146ee3/68747470733a2f2f61736369696e656d612e6f72672f612f3231313336302e706e67)

![Image](https://camo.githubusercontent.com/c1f93a14442849227322b30778fe993a2e924524af0f82dec2cacae2703a48dc/68747470733a2f2f61736369696e656d612e6f72672f612f3231313335302e706e67)

Ferramenta moderna e rápida de fuzzing.

Instalação:

```bash
go install github.com/ffuf/ffuf/v2@latest
```

Uso:

```bash
ffuf -u https://empresa.com/FUZZ -w wordlist.txt
```

Filtrar status 200:

```bash
ffuf -u https://empresa.com/FUZZ -w wordlist.txt -mc 200
```

---

# Dirsearch

Repositório:  
[https://github.com/maurosoria/dirsearch](https://github.com/maurosoria/dirsearch)

![Image](https://www.briskinfosec.com/themes/new_theme/ckeditor/plugins/imageuploader/uploads/533963f69.png)

![Image](https://miro.medium.com/v2/resize%3Afit%3A1400/0%2AhE-ozcXa5STSw_K0.png)

![Image](https://miro.medium.com/v2/resize%3Afit%3A1400/0%2A-kgzgkBI4RGBPvu4.png)

![Image](https://www.briskinfosec.com/themes/new_theme/ckeditor/plugins/imageuploader/uploads/534e622d9.png)

Instalação:

```bash
git clone https://github.com/maurosoria/dirsearch.git
cd dirsearch
pip3 install -r requirements.txt
```

Uso:

```bash
python3 dirsearch.py -u https://empresa.com
```

---

# 2. CONTENT DISCOVERY

Content Discovery busca:

- Arquivos ocultos
    
- Pastas
    
- Backups
    
- Endpoints não documentados
    

---

## HTTPX

Repositório:  
[https://github.com/projectdiscovery/httpx](https://github.com/projectdiscovery/httpx)

![Image](https://user-images.githubusercontent.com/8293321/135731750-4c1d38b1-bd2a-40f9-88e9-3c4b9f6da378.png)

![Image](https://www.python-httpx.org/img/httpx-request.png)

![Image](https://user-images.githubusercontent.com/38748801/170458774-e56156da-6e3a-448a-bceb-3a5cbbf8658b.png)

![Image](https://projectdiscovery.io/_next/image?q=75&url=https%3A%2F%2Fprojectdiscovery.ghost.io%2Fcontent%2Fimages%2F2023%2F01%2Frecon5-1.png&w=3840)

Instalação:

```bash
go install github.com/projectdiscovery/httpx/cmd/httpx@latest
```

Uso:

```bash
httpx -l subs.txt
```

Detectar status:

```bash
httpx -l subs.txt -status-code
```

---

## Aquatone

Repositório:  
[https://github.com/michenriksen/aquatone](https://github.com/michenriksen/aquatone)

![Image](https://static.packt-cdn.com/products/9781789952308/graphics/assets/36618d23-b47d-44c0-ab9a-972ef1ab43dc.png)

![Image](https://blog.cyberadvisors.com/hubfs/Imported_Blog_Media/I1tLPI3osKvC19WiqQhbNrB5hwuDobZ3TqBEWFL3YmOVlhnkL55ASprkexAVA9L3ppk1QsuhBVlpNX5mdhfuIJGBYzdZhgdcVhl8AgPFTdzkelivNSecwDAQopDsCTQjHTXly3EikZm9LCPWYbWtASZYF5b3kdY-.png)

![Image](https://www.datocms-assets.com/85623/1719570731-aquatone_similarity_view-1.png?auto=format)

![Image](https://miro.medium.com/v2/resize%3Afit%3A1400/1%2A0v_KhlqAEbDQaeFVjgjOMg.gif)

Tira screenshots automáticos.

Uso:

```bash
cat subs.txt | aquatone
```

---

## SecretFinder

Repositório:  
[https://github.com/m4ll0k/SecretFinder](https://github.com/m4ll0k/SecretFinder)

![Image](https://www.briskinfosec.com/assets/tooloftheday/138.jpg)

![Image](https://miro.medium.com/1%2AkdV73myzXbVaZSqut1GYAA.png)

![Image](https://i.imgur.com/D7MT2KL.png)

![Image](https://miro.medium.com/v2/resize%3Afit%3A1400/1%2AN9NqjtC2DMCDvxvlqyC4ag.jpeg)

Detecta:

- API keys
    
- Tokens
    
- Secrets em JS
    

Instalação:

```bash
git clone https://github.com/m4ll0k/SecretFinder.git
cd SecretFinder
pip3 install -r requirements.txt
```

Uso:

```bash
python3 SecretFinder.py -i https://empresa.com/app.js -o cli
```

---

# 3. PARAMETER DISCOVERY

Parameter Discovery identifica parâmetros que aceitam input do usuário.

Exemplo:

```
?id=
?user=
?file=
?redirect=
?callback=
```

---

## ParamSpider

Repositório:  
[https://github.com/devanshbatham/ParamSpider](https://github.com/devanshbatham/ParamSpider)

![Image](https://www.cobalt.io/hs-fs/hubfs/paramspider-example.png?height=360&name=paramspider-example.png&width=837)

![Image](https://raw.githubusercontent.com/0xKayala/ParamSpider/master/static/example.PNG)

![Image](https://raw.githubusercontent.com/0xKayala/ParamSpider/master/static/banner.PNG)

![Image](https://opengraph.githubassets.com/21ab9b11885fa75bc71467a303d9d4c2c1d1675d4bf316253ae02ba979d5fcff/devanshbatham/ParamSpider)

Instalação:

```bash
git clone https://github.com/devanshbatham/ParamSpider.git
cd ParamSpider
pip3 install -r requirements.txt
```

Uso:

```bash
python3 paramspider.py -d empresa.com
```

---

## GF

Repositório:  
[https://github.com/tomnomnom/gf](https://github.com/tomnomnom/gf)

![Image](https://miro.medium.com/1%2Av054Fm0JC2XeU6hLDoXjow.jpeg)

![Image](https://user-images.githubusercontent.com/85204383/180190920-b696cfdc-32db-49cc-9c5f-64b250c27665.jpg)

![Image](https://opengraph.githubassets.com/ad2d26a4d78618be16826c0b6da58ea26397cf4e877e1375a61e8845257e72ad/1ndianl33t/Gf-Patterns)

![Image](https://user-images.githubusercontent.com/18244131/107920520-ae519f00-6f9f-11eb-98ab-9360d2dd3c16.png)

Ferramenta para filtrar padrões.

Instalação:

```bash
go install github.com/tomnomnom/gf@latest
```

Uso:

```bash
cat urls.txt | gf xss
```

---

## Parth

Repositório:  
[https://github.com/s0md3v/Parth](https://github.com/s0md3v/Parth)

![Image](https://i.sstatic.net/z21Nz.png)

![Image](https://assets.apidog.com/blog/2024/03/path-parameter-example.png)

![Image](https://miro.medium.com/v2/resize%3Afit%3A1400/1%2AQiqEKe63dtX5GtRJCmFRMA.png)

![Image](https://user-images.githubusercontent.com/76661350/193249886-79f3d04a-47c0-4b4b-93a6-23c32cf762f1.png)

Instalação:

```bash
git clone https://github.com/s0md3v/Parth.git
cd Parth
pip3 install -r requirements.txt
```

Uso:

```bash
python3 parth.py -u https://empresa.com
```

---

# Tornando todos globais

Para qualquer ferramenta Go:

Mover para:

```bash
sudo mv ~/go/bin/* /usr/local/bin/
```

Para Python:

Criar alias:

```bash
sudo ln -s /home/kali/dirsearch/dirsearch.py /usr/local/bin/dirsearch
```

Dar permissão:

```bash
chmod +x /usr/local/bin/dirsearch
```

Agora funciona de qualquer diretório.
