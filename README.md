# LoL Randomizer

Sorteie times, posições e campeões de League of Legends entre amigos. Tudo roda no navegador, em um único arquivo HTML, sem conta, sem instalação e sem servidor.

**Site:** https://lol-randomizer-pro.netlify.app/

## O que o site faz

- **Dois modos de jogo**
  - **Partida Fechada:** você informa todos os participantes e o site divide em TIME AZUL e TIME VERMELHO.
  - **Contra Randoms:** você informa só o seu time. Nenhum adversário é criado.
- **De 1v1 a 5v5**, com a quantidade de campos de nome ajustada automaticamente.
- **Sorteios independentes:** times, posições e campeões têm botões próprios. Sortear de novo uma etapa invalida só o que depende dela.
- **Ordem fixa das posições:** TOP → JUNGLE → MID → ADC → SUPPORT, não importa a ordem dos nomes.
- **Banco com todos os campeões** e suas rotas possíveis, incluindo flex picks, sem repetir campeão na mesma partida sempre que houver opções.
- **Copiar resultado** em texto pronto para Discord e WhatsApp.
- **Gerar imagem** do resultado, com prévia e download em PNG.
- **Colar lista de nomes** de uma vez, sem digitar um por um.
- Funciona em computador e celular.

## Como usar

1. Escolha o **modo de jogo** e a **quantidade de jogadores** por equipe.
2. Clique em **Cadastrar jogadores** e digite os nomes.
3. Na tela de resultado, use os botões:
   - **Sortear times** (só na partida fechada)
   - **Sortear posições** (só no 5v5)
   - **Sortear campeões**
   - **Copiar resultado**
   - **🖼️ Gerar imagem**
   - **Nova tentativa de sorteio** e **Nova partida**

### Equipes com menos de 5 jogadores

Em 1v1, 2v2, 3v3 e 4v4 não existe sorteio de posição. O campeão é sorteado entre todos os campeões do banco, e o resultado aparece sem lane.

### Cadastro rápido

| Ação | Atalho |
|---|---|
| Ir ao próximo campo | `Enter` |
| Voltar ao campo anterior | `Shift` + `Enter` |
| Confirmar no último campo | `Enter` |
| Colar uma lista de nomes | `Ctrl` + `V` em qualquer campo |

Também dá para usar o botão **Colar lista**, que abre uma caixa maior para colar vários nomes e clicar em **Feito**. Os nomes podem estar separados por linha, vírgula, ponto e vírgula ou tabulação. Numeração e marcadores (`1.`, `2)`, `-`, `•`) são removidos. Se houver nomes demais, os que não cabem ficam de fora e o site avisa.

## Regras dos sorteios

- O sorteio dos times é totalmente aleatório, sem equilibrar por habilidade ou elo.
- Cada equipe recebe exatamente a quantidade configurada de jogadores, sem duplicações.
- Dentro de uma equipe, as posições não se repetem.
- Cada jogador recebe um campeão da lista da própria posição.
- Para evitar repetição com flex picks, as posições com menos opções sorteiam primeiro.
- Só se uma posição ficar sem opções novas é que o site permite repetir um campeão.
- Se os times forem sorteados de novo, posições e campeões antigos são descartados. Se as posições forem sorteadas de novo, os campeões são descartados.

## Atualizando o banco de campeões

Os dados ficam em um único bloco no começo do script, a constante `CHAMPION_DB`. Cada campeão é escrito como `Nome:ROTAS`:

| Letra | Rota |
|---|---|
| `T` | TOP |
| `J` | JUNGLE |
| `M` | MID |
| `A` | ADC |
| `S` | SUPPORT |

Exemplos: `Aatrox:T`, `Akali:MT`, `Lux:SM`.

As rotas são funções possíveis do campeão, não uma garantia de força no meta atual. Para adicionar um campeão ou mudar a rota de alguém, basta editar essa lista. A lógica dos sorteios não precisa mudar.

Se o retrato de um campeão novo não aparecer, o ID dele no Data Dragon pode ser diferente do nome. Nesse caso, adicione-o ao objeto `SPECIAL`, perto do `CHAMPION_DB`.

## Recursos externos e uso offline

Os sorteios funcionam sem internet. Estes recursos externos são só visuais:

| Recurso | Uso | Sem internet |
|---|---|---|
| Google Fonts (Marcellus e Inter) | Fontes do site | Usa fontes do sistema |
| Data Dragon (Riot Games) | Retratos dos campeões | Mostra a inicial do campeão |
| CommunityDragon | Ícones oficiais das posições | Usa ícones desenhados |

A imagem do resultado também usa esses retratos e ícones. Sem eles, ela é gerada com as alternativas acima.

## Tecnologias

HTML, CSS e JavaScript puros, em um único arquivo, sem bibliotecas nem etapa de build. A imagem é desenhada com Canvas no próprio navegador, sem geração por IA.

## Rodando localmente

Baixe o arquivo HTML, renomeie para `index.html` e abra no navegador. Não precisa de servidor.

## Publicando

Por ser um arquivo estático, basta enviar o `index.html` para qualquer hospedagem estática, como Netlify, GitHub Pages ou Vercel. No Netlify, dá para arrastar a pasta com o arquivo na tela de deploy.

## Aviso legal

O LoL Randomizer não é endossado pela Riot Games e não reflete as opiniões de ninguém oficialmente envolvido na produção ou no gerenciamento de propriedades da Riot Games. League of Legends e Riot Games são marcas registradas da Riot Games, Inc. Retratos e ícones pertencem à Riot Games.
