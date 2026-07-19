# Pesquisa de Satisfacao - LemosPassos

Sistema web simples para registrar pesquisa de satisfacao do restaurante, com
nome opcional, frequencia de visita, cardapio do dia, acesso administrativo e
exportacao manual em `.xlsx`.

## Como testar

Abra o arquivo `index.html` no navegador. O sistema funciona sem banco de dados
nesta primeira versao, salvando cardapio e respostas no `localStorage` do
proprio navegador.

Para publicar no GitHub Pages, envie estes arquivos para um repositorio e ative
o GitHub Pages apontando para a branch/pasta onde o `index.html` estiver.

## Acesso administrativo

Usuario padrao:

```txt
admin
```

Senha padrao:

```txt
admin1234
```

No painel administrativo e possivel:

- cadastrar o cardapio do dia;
- exportar respostas em `.xlsx` com aba de respostas e aba de indicadores;
- informar e-mails que serao usados futuramente no envio automatico quinzenal;
- apagar respostas salvas localmente neste navegador.

## Relatorio XLSX

A exportacao gera duas abas:

- **Respostas**: lista completa das respostas, com filtro automatico no Excel.
  Use os filtros das colunas **Data**, **Prato principal**, **Prato opcao**,
  **Guarnicao 1**, **Guarnicao 2** e demais campos para analisar periodos e
  pratos especificos.
- **Indicadores**: resumo com total de respostas, periodo, contagem de notas por
  pergunta, resumo geral por avaliacao, frequencia de visita, respostas por data
  e pratos/guarnicoes consumidos.

Nesta versao estatica, a biblioteca usada no navegador gera os dados prontos
para graficos, mas nao cria graficos reais dentro do arquivo com a mesma
confiabilidade do Excel desktop. Para visualizar graficos, abra a aba
**Indicadores** no Excel e insira graficos a partir das tabelas.

## Onde alterar o nome da unidade

Abra o arquivo `script.js` e altere esta linha dentro de `CONFIG`:

```js
unitName: "Restaurante Popular Lauro de Freitas",
```

## Onde alterar o logotipo

O logotipo atual esta em:

```txt
assets/logo-lemospassos.png
```

Para trocar, substitua esse arquivo por outro com o mesmo nome ou altere o
caminho no `script.js`, dentro de `CONFIG`:

```js
logoPath: "assets/logo-lemospassos.png",
```

## Onde alterar usuario e senha do ADM

Abra o arquivo `script.js` e altere:

```js
adminUser: "admin",
adminPassword: "admin1234",
```

Importante: nesta versao sem backend, esse login e apenas uma barreira simples
para teste. Quando houver banco de dados e hospedagem com servidor, o ideal e
criar autenticacao real no backend.

## Onde colocar os e-mails do envio futuro

Existem dois lugares preparados:

1. Pelo painel ADM, no campo **E-mails para receber relatorio quinzenal**.
2. Diretamente no arquivo `script.js`, na configuracao:

```js
futureReportEmails: "",
```

Exemplo:

```js
futureReportEmails: "gestor@empresa.com.br, qualidade@empresa.com.br",
```

Nesta primeira versao, o sistema ainda nao envia e-mail automaticamente. O campo
fica preparado para a fase futura com banco de dados, hospedagem e rotina
agendada.

## Como sera o envio automatico quinzenal futuramente

Para enviar o relatorio automaticamente a cada 15 dias, sera necessario adicionar
um backend ou servico agendado. Caminhos recomendados:

- Supabase com banco de dados e Edge Function agendada;
- servidor Node.js com cron e servico de e-mail;
- GitHub Actions agendado, lendo os dados de um banco externo;
- hospedagem serverless com SendGrid, Brevo ou outro provedor de e-mail.

Na fase atual, use a exportacao manual `.xlsx` pelo painel ADM.

## Observacao sobre os dados

Como o armazenamento atual e local, as respostas ficam apenas no navegador onde
foram registradas. Ao trocar de computador ou navegador, os dados nao aparecem.
Na proxima fase, isso deve ser substituido por banco de dados.

## Rodape

O rodape possui o texto **Desenvolvido por GDS** com link para:

```txt
https://instagram.com/guedesyc
```
