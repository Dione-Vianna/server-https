# Conceito de SSL, TLS e SSH

## Você precisa de três coisa muito importante

1. Uma entidade certificadora <br>
   [Let's Encrypt](https://letsencrypt.org/) <br>
   É a única no ramo que gera um certificado valido e gratuitamente.

2. Tem que ter um domínio <br>
   Aqui tem que gastar, foi o único que eu ainda não descobri um meio gratis <br>
   [Registo BR](https://registobr.com)
3. Um terceiro que valide o certificado <br>
   Uma entidade que vai validar o certificado

---

## Mãos a obra

Vamos precisar de um cliente <strong>ACME</strong> <br>
Eu escolhi o <strong>Certbot</strong> você pode escolher o de sua preferência.

### Install Certbot

[Certbot](https://certbot.eff.org/)

- Linux

```properties
sudo add-apt-repository ppa:certbot/certbot
sudo apt-get update
sudo apt-get install certbot
```

- Mac

```properties
brew install certbot
```

- Windows

```
Só baixa o executável depois next next...
```

Apos terminar de instalar certbot, rode o comando no terminal

```properties
certbot certonly --standalone
```

OBS: A porta 80 tem que esta livre então caso de erro verifica se tem algum programa rodando nesta porta é para o processo

Ele vai pedir alguns dados para você como email e domínio, se tudo estiver certo ele vai gera o certificado é vai lhe mostra o caminho onde o mesmo esta, pegue esse caminho e coloque no seu arquivo principal, no meu caso o <strong>index.js</strong>

```javascript
const privateKey = fs.readFileSync('caminha-do-arquivo/privkey.pem', 'utf8');
const certificate = fs.readFileSync('caminha-do-arquivo/cert.pem', 'utf8');
const ca = fs.readFileSync('caminha-do-arquivo/chain.pem', 'utf8');
```
