# Atividade 2 – Braço Robótico

**Disciplina:** Computação Gráfica
**Atividade:** Braço Robótico (grafo de cena)
**Integrantes:** Vinicius da Motta Campos

## Descrição

A cena foi montada com a hierarquia:

`base → ombro (Object3D) → braço laranja`
`                        → cotovelo (Object3D) → antebraço azul → garra cinza`

- O **ombro** é um `Object3D` vazio no topo da base (y = 0.2 no sistema da base). O **braço** (altura 1.2) é filho do ombro e foi deslocado em 0.6 para cima, de modo que sua ponta de baixo fique no pivô.
- O **cotovelo** é outro `Object3D`, filho do ombro, na ponta de cima do braço (y = 1.2). O **antebraço** (altura 1.0) é filho do cotovelo e deslocado em 0.5.
- A **garra** é filha do antebraço, na sua ponta (y = 0.5 + 0.075).
- **Controles:** A/D giram a base em torno de Y, W/S giram o ombro em torno de Z e I/K giram o cotovelo em torno de Z. Todas as rotações são multiplicadas por `deltaTime`.

A captura com o braço dobrado (tecla **P**) está em `capturas/resultado.png`.

## Resposta da questão

**Por que foi necessário utilizar pivôs em vez de simplesmente girar diretamente as caixas?**

Uma caixa gira em torno do seu próprio centro, mas uma articulação precisa girar em torno de uma extremidade, no ombro ou no cotovelo. O `Object3D` vazio funciona como esse ponto de rotação: ele fica exatamente na junta, e a caixa é deslocada em relação a ele. Como o pivô é pai das partes seguintes, girar o ombro leva junto o cotovelo, o antebraço e a garra, e girar o cotovelo leva o antebraço e a garra. Se girássemos as caixas diretamente, cada uma giraria em torno do próprio centro, as peças se descolariam nas juntas e as partes seguintes não acompanhariam o movimento.
