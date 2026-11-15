# Portfólio de Gabriel Medeiros

Portfólio pessoal estático, feito com HTML e CSS para praticar um laboratório introdutório de Docker no GitHub Codespaces. Não há JavaScript, frameworks ou backend.

## Arquivos

- `index.html`: conteúdo da página, em português brasileiro, com apresentação, interesses e links de contato.
- `styles.css`: estilo responsivo da página, carregado por um caminho relativo no HTML.
- `Dockerfile`: define a imagem Docker do site usando Nginx e copia os dois arquivos estáticos para a pasta servida pelo Nginx.
- `.dockerignore`: limita o contexto de construção a `index.html`, `styles.css` e `Dockerfile`.
- `.devcontainer/devcontainer.json`: quando presente, configura o ambiente de desenvolvimento usado pelo Codespaces, como ferramentas e opções do container de desenvolvimento. É separado do container Nginx que serve o site.
- `README.md`: explica o projeto e como executá-lo e publicá-lo.

## Imagem, container e Nginx

Uma **imagem** é um pacote com os arquivos e as instruções necessários para executar um programa. O comando `docker build` cria a imagem deste projeto.

Um **container** é uma instância em execução criada a partir de uma imagem. Ele mantém o site rodando enquanto o container estiver ativo.

O **Nginx** é o servidor web incluído na imagem escolhida. Neste projeto, ele entrega os arquivos HTML e CSS aos navegadores; não há aplicação de backend.

## Executar no Codespaces

No terminal, na raiz do repositório, construa a imagem:

```sh
docker build -t meu-portfolio:v1 .
```

Inicie um container com a porta 80 do Nginx disponível na porta 8080 do Codespaces:

```sh
docker run -d -p 8080:80 --name portfolio meu-portfolio:v1
```

Abra o link da porta **8080** na aba **Ports** do Codespaces para acessar o portfólio.

Ao terminar, pare e remova o container:

```sh
docker stop portfolio
docker rm portfolio
```

## Publicar no GitHub Pages

Nas configurações do repositório, habilite o GitHub Pages usando a branch `main` e a pasta `/(root)`. Como o login e o nome deste repositório são `gabrielmedeirous`, o endereço do site é:

<https://gabrielmedeirous.github.io/>

O GitHub Pages **não executa nosso container**; ele publica os mesmos arquivos estáticos HTML e CSS diretamente do repositório.

## Ideias para o futuro

Imagens, JavaScript e animações podem ser considerados como ideias para uma evolução futura. Não fazem parte desta versão simples.
