# Atividade 1 – Mini Sistema Solar

**Disciplina:** Computação Gráfica
**Atividade:** Mini Sistema Solar (transformações geométricas)
**Integrantes:** Vinicius da Motta Campos

## Descrição

O programa desenha um Sol, um planeta e uma Lua usando apenas `make_translation`, `make_rotation_z` e `make_scale`, combinadas com o operador `@`.

- **Sol:** `R(anguloSol) @ S(0.25)`, girando em torno do próprio centro.
- **Planeta:** `R(anguloOrbita) @ T(0.6, 0, 0) @ R(anguloRotacaoPlaneta) @ S(0.1)`. Orbita o Sol com raio 0.6 e gira no próprio eixo com velocidade diferente da órbita.
- **Lua:** reaproveita a matriz de órbita do planeta e acrescenta sua própria órbita: `R(anguloOrbita) @ T(0.6,0,0) @ R(anguloOrbitaLua) @ T(0.2,0,0) @ S(0.05)`. Assim ela acompanha o planeta e orbita com raio 0.2.
- **Teclado:** as setas ↑ e ↓ aumentam e diminuem `velocidadeOrbita` (multiplicado por `deltaTime`), e `max(0.0, ...)` impede que ela fique negativa.

A captura do resultado (tecla **P**) está em `capturas/resultado.png`.

## Resposta da questão

**Por que a órbita utiliza `R @ T` e a rotação própria do planeta fica à direita da translação?**

Em uma expressão `A @ B @ ponto`, a matriz mais à direita é aplicada primeiro. Na órbita, `R @ T` primeiro afasta o planeta da origem (a translação) e depois gira esse ponto em torno da origem, onde está o Sol. É essa rotação que faz o planeta percorrer um círculo de raio 0.6. A rotação própria fica à direita da translação, então é aplicada antes dela, quando o planeta ainda está na origem. Por isso ele gira em torno do próprio centro e só depois é levado para a posição da órbita. Se a rotação própria ficasse à esquerda da translação, ela giraria o planeta em torno do Sol e não em torno de si mesmo.
