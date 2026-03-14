# Como o navegador interpreta HTML, CSS e JavaScript

Este documento explica **como o navegador funciona internamente**, como ele interpreta **HTML**, **CSS** e **JavaScript**, como funciona **uma tag**, **folhas de estilo**, **cascata do CSS** e como tudo isso vira pixels na tela.

---

## 1) O que acontece quando você acessa um site

Quando você digita um endereço no navegador e pressiona Enter, o servidor devolve arquivos (HTML, CSS, JS). O navegador então inicia o processo de renderização.

### Fluxo geral de renderização do navegador

![Pipeline de renderização do navegador](sandbox:/mnt/data/browser_render_pipeline.png)

### Passo a passo:

1. O navegador recebe o **HTML** (resposta HTTP).
    
2. O **parser HTML** analisa o texto e cria o **DOM**.
    
3. O navegador recebe o **CSS** (externo, interno ou inline).
    
4. O **parser CSS** cria o **CSSOM**.
    
5. O navegador combina **DOM + CSSOM** e cria o **Render Tree**.
    
6. Calcula **Layout** (posição e tamanho dos elementos).
    
7. Executa **Paint & Composite** (pintura dos pixels na tela).
    

---

## 2) HTML: como o navegador entende a estrutura da página

HTML não é linguagem de programação. Ele descreve **estrutura e significado**.

Exemplos de significado:

- `<h1>` → título
    
- `<p>` → parágrafo
    
- `<a>` → link
    
- `<form>` → formulário
    
- `<input>` → campo de entrada
    

O navegador transforma o HTML em uma estrutura chamada **DOM (Document Object Model)**, organizada como uma **árvore**.

Essa árvore é usada por:

- CSS (para aplicar estilos)
    
- JavaScript (para manipular elementos)
    
- Motor de renderização (para desenhar a tela)
    

---

## 3) Como funciona uma tag HTML (anatomia completa)

Abaixo está a estrutura real de uma tag HTML.

### Exemplo prático

```html
<a href="/login" class="btn" target="_blank">Entrar</a>
```

### Anatomia visual da tag

![Anatomia de uma tag HTML](sandbox:/mnt/data/html_tag_anatomy.png)

### Explicação:

- **Tag de abertura**: `<a>`
    
- **Atributos**:
    
    - `href` → destino do link
        
    - `class` → usado por CSS e JS
        
    - `target` → comportamento (nova aba)
        
- **Conteúdo**: `Entrar`
    
- **Tag de fechamento**: `</a>`
    

### Tags sem fechamento (auto-fechadas)

```html
<img src="foto.jpg" alt="imagem">
<input type="email" name="email">
```

---

## 4) CSS: o que é uma folha de estilo

CSS define **como os elementos aparecem**:

- cores
    
- fontes
    
- espaçamento
    
- posicionamento
    
- animações
    

### Formas de usar CSS

1. **CSS externo**
    

```html
<link rel="stylesheet" href="style.css">
```

2. **CSS interno**
    

```html
<style>
  body { background: black; }
</style>
```

3. **CSS inline**
    

```html
<p style="color:red;">Texto</p>
```

---

## 5) Estrutura de uma regra CSS

Uma regra CSS sempre tem:

```css
seletor {
  propriedade: valor;
}
```

Exemplo real:

```css
.btn {
  background-color: black;
  color: white;
  padding: 10px;
}
```

- `.btn` → seletor de classe
    
- `background-color`, `color`, `padding` → propriedades
    
- valores → como o navegador deve desenhar
    

---

## 6) CSS na base: cascata, especificidade e prioridade

Quando várias regras CSS atingem o mesmo elemento, o navegador precisa decidir **qual vence**.

### Cascata do CSS (prioridade)

![Cascata e especificidade do CSS](sandbox:/mnt/data/css_cascade_specificity.png)

### Regras principais:

1. **User Agent Stylesheet**  
    Estilos padrão do navegador.
    
2. **CSS do site (autor)**  
    CSS externo, interno e inline.
    
3. **Ordem no código**  
    Se a especificidade for igual, a regra escrita **mais abaixo vence**.
    
4. **Especificidade**
    
    - `#id` vence `.classe`
        
    - `.classe` vence `tag`
        
5. **!important**
    

```css
p { color: red !important; }
```

Força prioridade máxima (usar com cuidado).

---

## 7) DOM, CSSOM e JavaScript trabalhando juntos

O navegador cria duas estruturas principais:

- **DOM** → estrutura do HTML
    
- **CSSOM** → regras de estilo
    

Essas duas estruturas são combinadas.

### Visualização da interação

![DOM, CSSOM e JavaScript](sandbox:/mnt/data/dom_cssom_js.png)

### O papel do JavaScript

JavaScript:

- lê o DOM
    
- altera o DOM
    
- altera classes e estilos
    
- reage a eventos (click, submit, input)
    

Quando o JS muda algo:

- o navegador pode recalcular layout
    
- pode repintar a tela
    
- pode recompor camadas
    

---

## 8) JavaScript: dando vida à página

JavaScript é o que torna a página **interativa**.

Exemplo simples:

```html
<input id="email">
<button id="btn">Enviar</button>

<script>
  document.querySelector("#btn").addEventListener("click", () => {
    const email = document.querySelector("#email").value;
    console.log(email);
  });
</script>
```

- O JS acessa o DOM
    
- Escuta eventos
    
- Executa lógica
    
- Pode enviar dados ao backend via HTTP
    

---

## 9) Resumo final (bem direto)

- **HTML** → estrutura → vira **DOM**
    
- **CSS** → estilo → vira **CSSOM**
    
- **DOM + CSSOM** → **Render Tree**
    
- Depois:
    
    - Layout
        
    - Paint
        
    - Composite
        
- **JavaScript** pode alterar tudo isso dinamicamente
    

---

## Imagens usadas no documento

- Renderização:  
    `browser_render_pipeline.png`
    
- Anatomia de tag:  
    `html_tag_anatomy.png`
    
- DOM, CSSOM e JS:  
    `dom_cssom_js.png`
    
- Cascata do CSS:  
    `css_cascade_specificity.png`
    
