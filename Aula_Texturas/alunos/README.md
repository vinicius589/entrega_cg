# Atividade 3 – Cubo com Satélite Texturizado

**Disciplina:** Computação Gráfica
**Atividade:** Cubo com Satélite Texturizado (texturas)
**Integrantes:** Vinicius da Motta Campos

## Descrição

- O **cubo principal** usa a textura `mosaico.png`.
- O **satélite** é um segundo cubo com `grade_uv.png` e `repeatUV = [2,2]`. Ele é **filho** do cubo principal (`self.mesh.add(self.satelite)`), por isso acompanha a rotação dele e orbita.
- O satélite é posicionado primeiro (`setPosition([1.3, 0, 0])`) e só depois escalado (`scale(0.4)`). Assim a escala não reduz a distância de 1.3 ao centro.
- As setas ↑ e ↓ aumentam e diminuem `self.velocidade`, sempre multiplicadas por `deltaTime`.
- O satélite gira em torno do próprio eixo X a 2 rad/s (`rotateX(2 * deltaTime)`).

A captura do resultado (tecla **S**) está em `capturas/resultado.png`.

## Resposta da questão

**Qual é o papel das coordenadas UV em uma textura e qual é o efeito de `repeatUV = [2,2]`?**

As coordenadas UV são pares (u, v), em geral entre 0 e 1, associados a cada vértice do modelo. Elas dizem qual ponto da imagem corresponde a cada ponto da superfície, ou seja, definem como a imagem 2D é "colada" na geometria 3D. Com `repeatUV = [2,2]`, essas coordenadas são multiplicadas por 2 em cada direção. A imagem passa a se repetir duas vezes na horizontal e duas na vertical em cada face, formando 4 cópias menores da textura no lugar de uma só.
