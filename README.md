# Treze

Microjogo educativo sobre a **síndrome de Patau** (trissomia do cromossomo 13),
em português do Brasil. Roda inteiramente no navegador — sem servidor, sem
cadastro, sem coleta de dados.

**Jogar:** https://SEU-USUARIO.github.io/treze-patau/

## O que é

Um quiz que não é só um quiz. Depois de escolher a resposta, quem joga declara
se **tem certeza** ou se **está chutando** — certeza errada custa ponto, chute
honesto não custa nada. No fim saem duas notas: quanto acertou, e o quanto foi
honesto sobre o que não sabia.

Os pontos são moeda e destravam outras atividades:

| Atividade | Custo | O que é |
|---|---|---|
| **Treze** | grátis | 13 perguntas sorteadas de um banco de 33, com aposta de confiança |
| **Cariotipagem** | ◆25 | Parear 19 cromossomos e achar o número que veio em três |
| **Mito ou Fato** | ◆45 | 60 segundos, combo até ×4, erro tira 3 segundos |
| **Certeza Absoluta** | ◆90 | Só certeza permitida, um erro encerra a corrida |
| **Boliche 13** | ◆35 + ◆8/ficha | Boliche com física: 6 pares de pinos e um sozinho |

Há ainda um álbum de 13 cartas, cinco patentes de progressão, trilha sonora
gerada no navegador e efeitos sonoros — tudo sintetizado, sem arquivo de áudio.

## Estrutura

    index.html    o jogo inteiro: HTML, CSS e JavaScript num arquivo só
    .nojekyll     impede o GitHub Pages de processar o arquivo

Nenhuma dependência, nenhuma etapa de build. Abrir o `index.html` no navegador
já roda. O único recurso externo são as fontes do Google Fonts.

## Onde mexer no conteúdo

Tudo dentro de `index.html`, no início da tag `<script>`:

- `const Q = [...]` — as 33 perguntas do quiz (enunciado, alternativas, índice
  da correta, explicação e título da carta)
- `const MITOS = [...]` — as 35 afirmações do Mito ou Fato (`m: true` = mito)
- `const DEVS = [...]` — as idealizadoras que aparecem na abertura

### Colocar as fotos das idealizadoras

Em `const DEVS`, preencha o campo `img` com o caminho da imagem:

```js
const DEVS = [
  { nome: "Nome real", papel: "criação e conteúdo", img: "fotos/pessoa1.jpg", face: {...} },
  ...
];
```

Coloque as imagens numa pasta `fotos/` ao lado do `index.html`. Quadradas,
de preferência 400×400. Enquanto `img` for `null`, o jogo desenha um retrato
provisório em SVG.

## Vários jogadores

O jogo não tem servidor: cada pessoa roda a própria cópia no navegador dela e o
progresso fica no `localStorage` do aparelho. Não existe limite de jogadores
simultâneos e ninguém interfere no jogo de ninguém.

## Aviso

Jogo educativo. **Não substitui orientação de profissionais de saúde.** O
conteúdo das perguntas deve ser revisado por profissional qualificado antes de
divulgação ampla, e as fontes ainda precisam ser verificadas e incluídas.
